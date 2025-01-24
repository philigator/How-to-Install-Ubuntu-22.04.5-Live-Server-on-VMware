# How to Install Ubuntu 22.04.5 Live Server on VMware

**Note:** If any step does not include specific instructions for a particular setting, use the default option provided by VMware.

---

## Step 1: Create the Virtual Machine

1. Open VMware Player and click **Create a New Virtual Machine**.

      ![image](https://github.com/user-attachments/assets/5727d4fe-b9d6-453c-9019-2de91b37348b)

2. Select **Custom (advanced)** and click **Next**.

      ![image](https://github.com/user-attachments/assets/a7c80cfc-9513-4ba3-a160-a8b6523b3e1e)

3. On the **Choose the Virtual Machine Hardware Compatibility** window, click **Next**.
4. On the **Guest Operating System Installation** window:
    - Select **Installer disc image file (ISO)**.
    - Browse and select the downloaded `ubuntu-22.04.5-live-server-amd64.iso` file.
    - Click **Next**.

      ![image](https://github.com/user-attachments/assets/7d23a927-eac1-40d8-ad6a-4d8e41e7d080)

---

## Step 2: Configure Virtual Machine Settings

6. On the **Name the Virtual Machine** window:
    - Enter a recognizable name (e.g., "Ubuntu 22.04 Server").
    - Choose a folder location for the virtual machine.
    - Click **Next**.

      ![image](https://github.com/user-attachments/assets/736d47ce-887b-4cf5-9dfb-e584efb6a9d0)

7. On the **Processor Configuration** window:
    - Allocate at least **2 processors** and **1 core per processor**.
    - Click **Next**.

      ![image](https://github.com/user-attachments/assets/e16556d3-2fbd-4007-a9bf-1e2ba0c77e58)

8. On the **Memory for the Virtual Machine** window:
    - If your system has **16GB or more of RAM**, allocate at least **4GB (4096MB)**.
    - If your system has less than **16GB of RAM**, allocate **2GB (2048MB)**. Note that performance may be slower with less memory.
    - Click **Next**.

      ![image](https://github.com/user-attachments/assets/dfab02a9-83e3-448b-9c84-c8bce8fdb08b)

9. On the **Network Type** window:
    - **Bridged**: Use this if you want the virtual machine to have direct access to your network, appearing as a separate device. Ideal for testing or when a unique IP address is required.
    - **NAT**: Use this if you prefer the virtual machine to share the host's IP address, providing easier setup and added security behind the host's firewall.
    - Click **Next**.

      ![image](https://github.com/user-attachments/assets/3bd68cdf-be48-4e4f-9c83-96d75d009bdb)

10. For the following windows, keep the default options:
    - **Select I/O Controller Types**: Click **Next**.
    - **Select a Disk Type**: Click **Next**.
    - **Select a Disk**: Choose **Create a new virtual disk** and click **Next**.
11. On the **Specify Disk Capacity** window:
    - Set the disk size to at least **20GB**.
    - Select **Split virtual disk into multiple files**.
    - Click **Next**.

      ![image](https://github.com/user-attachments/assets/9d9d3c34-6771-4586-b972-860e7d5c2d47)

12. On the **Specify Disk File** window, click **Next**.
13. Review the virtual machine settings and click **Finish**.

---

## Step 3: Install Ubuntu 22.04.5 Live Server

14. Select the newly created virtual machine and click **Power on this virtual machine**.
15. Once the installer loads, follow the on-screen prompts:
    - Select your preferred **language** (default is English).
    - Select your **keyboard layout** (default is English).
    - Choose **Install Ubuntu Server**.

      ![image](https://github.com/user-attachments/assets/7f4a6b54-d6eb-4c97-8079-aca6caa9f6c8)

16. On the **Network configuration** screen:
    - Choose the network interface to configure.
        
    - **For Static IP:**
        
        - Select **Edit IPv4** and set the method to **Manual**.
        
        ![image](https://github.com/user-attachments/assets/c76fba7b-0738-479a-9f50-65c5263f7464)

        ![image](https://github.com/user-attachments/assets/4a0b59ec-4d87-4670-bf11-e8bdd298b6e1)

        - Enter the static IP address, subnet mask, gateway, and DNS server. For example:
            - IP Address: `192.168.1.100`
            - Subnet Mask: `255.255.255.0`
            - Gateway: `192.168.1.1`
            - Nane Server: `8.8.8.8`
        - Save changes and return to the network configuration menu.
        
        ![image](https://github.com/user-attachments/assets/f693b388-6769-4fb0-8b10-3dcaa2a13f0f)


    - **For DHCP:**
        
        - Leave the default settings to use dynamic IP assignment via DHCP.
    - After configuring your choice, click **Done** to continue.
        

**Note:**

- **Static IP** is recommended if you need a consistent network address, such as for hosting a server, accessing the VM remotely, or connecting to specific devices on your network.
- **DHCP** is ideal for simpler setups where the network assigns an IP automatically and you don't require a fixed address. This is easier to configure but may result in a different IP address after reboots or network changes.
- If you are using DHCP you can skip the "How to Find the Default Gateway in VMware Workstation" section.

### How to Find the Default Gateway in VMware Workstation

To determine the default gateway for your virtual machine's network in VMware Workstation, follow these steps:

I. **Access Virtual Network Editor**:
    
   - In the menu at the top of the VMware Workstation
   - Click "Edit" and select "Virtual Network Editor".

      ![image](https://github.com/user-attachments/assets/44827be6-5644-4128-b9b9-a1ac01627b71)

II. **Select the Network Type**:
    
   - Look for the virtual network (e.g., `VMnet8` for NAT or `VMnet0` for Bridged).
   - For a NAT network, click on "Name:VMnet8" "Type: NAT"
III. **Find the Default Gateway**:
    
   - For a NAT network, click on "NAT Setting..."
   - Then copy down the "Subnet IP" and "Gateway IP".
   - For a **Bridged** network, the default gateway is the same as your host machine’s network gateway.

      ![image](https://github.com/user-attachments/assets/7f137c5f-43ab-46d8-bc39-1263f9e8c7a0)

      ![image](https://github.com/user-attachments/assets/90a30806-bf49-4d40-baf1-edfd7dd20ee5)

IV. **Use the Gateway**:
    
   - Use the displayed gateway IP address when configuring your static IP settings inside the virtual machine.

17. On the **Storage configuration** screen:
    - Select **Use an entire disk** and press Enter.
    - Confirm the disk selection and press Enter.
    - Select **Done** and confirm changes by selecting **Continue**.

      ![image](https://github.com/user-attachments/assets/bca75459-c132-4b07-b1d9-0bb675f11122)

      ![image](https://github.com/user-attachments/assets/6be65f13-fc35-4960-a397-c528b03a6814)

18. On the **Profile setup** screen:
    - Enter a username, password, and hostname for the server.
    - Click **Done** to proceed.
19. On the **SSH setup** screen:
    - Select whether to install OpenSSH (recommended for remote access).
    - Click **Done** to continue.

      ![image](https://github.com/user-attachments/assets/fa7a35eb-ad9a-471b-9e01-46821fa8a18c)

20. On the **Featured Server Snaps** screen:
    - Choose additional software to install, or leave it blank for now.
    - Click **Done** to proceed.
21. Wait for the installation process to complete.

---

## Step 4: Complete Installation

22. Once the installation is complete, select **Reboot Now** to restart the virtual machine.
    - If it hangs on “removing the CDROM” just press Enter
23. Log in with the username and password you configured earlier.

---

This guide ensures users can set up an Ubuntu server efficiently while understanding optional configurations like VMware Tools. Let me know if you need further refinements!
