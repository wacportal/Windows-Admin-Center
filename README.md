# Windows Admin Center

You can update non-preview editions of Windows Admin Center either via Microsoft Update or by manually downloading and installing the software. Each non-preview release remains supported for 30 days following the release of the subsequent non-preview version. Refer to our support policy for additional details.

## Prerequisites

Before installing Windows Admin Center, ensure the following requirements are met:

* A Windows PC or server for the installation of Windows Admin Center.

* Administrative privileges or equivalent permissions on the target machine.

* Optional: An SSL certificate intended for *Server Authentication (1.3.6.1.5.5.7.3.1)*. For testing purposes, a self-signed certificate is acceptable, but for production deployments, use a certificate issued by a trusted certificate authority. If you don’t have a certificate, the Windows Admin Center installer can create a self-signed certificate valid for 60 days.

## Determine your installation type

Check the [installation options](*) including the [supported operating systems](*). To deploy Windows Admin Center on an Azure virtual machine, see [Deploy Windows Admin Center in Azure](*).

## Install Windows Admin Center

### Desktop Experience

To install Windows Admin Center on a machine with the Windows Server Desktop Experience, follow these instructions:

1. Open the **Start** menu and type **Windows Admin Center Setup** into the search bar.

2. Choose **Windows Admin Center Setup** from the **Best match** list.

3. In the **Get started with Windows Admin Center** window, if you accept the license terms, click **Next** to continue.

4. The installer will automatically download to the *Downloads* folder. When the download is complete, click **Install**. This action launches the installer from the Downloads folder.

5. In the **Welcome to the Windows Admin Center setup wizard** window, select **Next**.

6. In the **License Terms and Privacy Statement** window, if you agree with the terms, select **I accept these terms and understand the privacy statement**, then click **Next** to initiate the installation.

7. In the **Select installation mode** window, choose **Express setup**, then select **Next**.

8. In the **Select TLS certificate** window, select the option appropriate for your scenario, then click **Next**.

> ### Note
>
> You must specify which Transport Layer Security (TLS) certificate Windows Admin Center should use. If you already have a certificate, it must reside in the `LocalMachine\My` certificate store. For testing purposes, the installer can create a self-signed certificate valid for 60 days.

9. In the **Automatic updates** window, pick your preferred update option, then click **Next**.

10. In the **Send diagnostic data to Microsoft** window, choose your preference, then click **Next**.

11. Review the **Ready to install** window, then select **Install** to begin the installation.

12. After installation completes, select **Start Windows Admin Center**, then click **Finish**.

13. Sign in with an administrator account to start using Windows Admin Center.

### Server Core

To install Windows Admin Center on a machine running Windows Server Core or via PowerShell, follow these steps:

1. Sign in to the machine. On Server Core, open the SConfig menu, select option **15**, and press <kbd>Enter</kbd> to launch a PowerShell session. On Desktop Experience, remote desktop into your VM and open PowerShell.

2. Download the Windows Admin Center installer and copy it to your system using PowerShell:

```powershell
$parameters = @{
     Source = "https://aka.ms/WACdownload"
     Destination = ".\WindowsAdminCenter.exe"
}
Start-BitsTransfer @parameters
```

3. To install Windows Admin Center, run:

```powershell
Start-Process -FilePath '.\WindowsAdminCenter.exe' -ArgumentList '/VERYSILENT' -Wait
```

4. You may also need to start the Windows Admin Center service:

```powershell
Start-Service -Name WindowsAdminCenter
```

Windows Admin Center is now installed and ready for use on your machine.
