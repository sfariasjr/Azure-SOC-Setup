# Azure-SOC-Setup
![image](https://user-images.githubusercontent.com/109401839/230745596-57cee9bd-687c-427d-b0db-d1080df77f7e.png)

# Azure Setup

### First, we will set up our Azure subscription and resources. Then, we will cover topics such as failed authentication, log observation, and an overview of Azure Active Directory, including users, groups, and access management.

#### Environments and Technologies Utilized 

- Microsoft Azure
- SQL Server
- Event Viewer
- Operating System: Windows 10 Pro (21H2)

## Resources & SQL Server Vulnerabilties

Actions and Observations:
1. Create a Windows 10 Pro virtual machine.
2. Assign the name "RG-Cyber-Lab" to the resource group.
3. Set the name of the virtual network as "Lab-VNet".
4. Double-check the virtual machine settings and proceed with creation.

Configure Network Security Group:
- Set up a Layer 4 firewall (Network Security Group) to allow all inbound traffic.
- This firewall is intentionally designed to attract threat actors such as hackers, bots, and attackers to try accessing our virtual machine.

Resource Group and Network Security Group:
- Access the resource group to view associated components of the virtual machine being created.
- Locate and edit the network security group, either through search or within the resource groups.

Inbound Security Rule:
- Create an inbound security rule called "DangerAllInBound" with the settings "Any" to handle all types of traffic.

Ping the VM's IP Address:
- Open the command prompt (CMD) and attempt to ping the IP Address of the VM.
- Verify if the ping command was successful.

Remote into the VM:
- Use "Remote Desktop Connection" to establish a remote connection to the VM.
- This step is necessary to change the firewall setting within the VM.

Turn off Windows Firewall:
- After logging in to the VM, search for "wf.msc" in the start menu to launch the "Windows Defender Firewall Advanced Security" program.
- Access "Windows Defender Firewall Properties".
- Disable the "Firewall State" on each tab.
- For now, ignore IPSEC settings.

Observe the changes in CMD:
- Return to the command prompt (CMD) and observe any changes or improvements.

Install SQL Server Evaluation:
- Download the SQL Server Evaluation from the provided link.
- Install the .exe file and select the "Download Media" or "ISO" option.
- Open the designated folder and proceed to mount the media.
- The mounted media will appear as a disk file under the "This PC" side panel.

Installation of SSMS (SQL Server Management Studio):
- Execute the "sql install" command to begin the installation process.
- During installation, select "Mixed Mode" to enable both online and local logins to the SQL Server.
- The default username is "sa" with the password ```LabTest12345``` (You can choose a different password, but make sure to document it).
- Add your current user and enter the associated password.
- Complete the installation to establish connectivity to the SQL Database.

Downloading Server Management Studio:
- Proceed to download Server Management Studio for further operations.

Configuring Audit Object Access Setting:
- Open a command prompt with administrative permissions.
- Navigate to the Command Prompt from the Start menu and select "Run as administrator".
- If prompted by the User Account Control dialogue box, select "Continue".
- Enable auditing from SQL Server by executing the following statement in the command prompt:

```
audit-pol /set /subcategory: "application generated" /success:enable /failure:enable
```

Enabling Logging for SQL Server:
- Open a command prompt with administrative permissions.
- Execute the necessary command to enable logging for SQL Server to be ported into Windows Event Viewer.

Closing the Command Prompt:
- Close the command prompt window.
