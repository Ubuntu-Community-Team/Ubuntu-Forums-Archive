---
title: "eToken PKI client 3.65 installation under Feisty Fawn"
date: 2007-05-23
forum: Server Platforms
---

### Post by pbarbier on 2007-05-23
Here are the steps to install Aladdin eToken PKI client 3.65 under Ubuntu Feisty Fawn


------------------------------------------------------------
Note
------------------------------------------------------------

I did all the following being logged in as root, what is rather unusual under Ubuntu where we rather use the sudo command. If you prefer use sudo, you'll know where to add it.

If you prefer use root but don't know how to make root be operational, here is how to proceed
- Log on with your userid
- Open a terminal
- Execute the following command:

# sudo passwd root
- Enter your userid password
- Enter the root password
- Confirm the root password

From now on, you can use root. From a console, just enter "su" with no argument or "su root".


------------------------------------------------------------
PCSC Lite installation
------------------------------------------------------------

The 2 following packages are prerequisite:
- libc6-dev
- libusb-dev
Use Synaptic or apt-get to do so.
Ex:
# apt-get install libc6-dev
# apt-get install libusb-dev


------------------------------------------------------------
Build
------------------------------------------------------------

Download pcsc-lite-1.4.1 from [http://www.linuxnet.com](http://www.linuxnet.com)
Extract files from pcsc-lite-1.4.1.tar.gz:
# tar zxvf pcsc-lite-1.4.1.tar.gz

Build PCSC:
# ./configure --enable-libusb
# make
# make install

Start the pcscd daemon:
# /usr/local/sbin/pcscd

Check that the daemon is running:
# ps -e | grep pcsc

You should get an ouput like this one:
# 20214 ?        00:00:00   pcscd


------------------------------------------------------------
eToken installation
------------------------------------------------------------

Get eToken installation files.
Extract files from etoken-3-65.3-linux-Fedora-i386.tar.gz :
# tar zxvf etoken-3-65.3-linux-Fedora-i386.tar.gz

Edit file Installer.pm:
# vi ./Installer.pm (or gedit ./Installer.pm to use an easier text editor)
Locate line
  my @known=qw ( suse enterprise fedora );
Change it to
  my @known=qw ( Ubuntu suse enterprise fedora );

Create the following symbolic link:
# ln -s /usr/local/lib/libpcsclite.so /usr/lib/libpcsclite.so.0

To install eToken for 4 readers, execute the following command:
# ./petoken install 4

Output will look like this one:
# Starting Aladdin eTokend daemon: 
# 
# Starting pcscd daemon: 
# 
# Modifying /etc/ld.so.conf
# Aladdin Etoken RTE installation finished
# Starting Aladdin etsrvd daemon: 

If you want to uninstall eToken, use the following command:
# ./petoken uninstall


------------------------------------------------------------
Creation of file 01-etoken.rules
------------------------------------------------------------

In order to be able to plug and unplug your eToken, you need to make a file called 01-etoken.rules in the /etc/udev/rules.d folder.
Here are the contents of this file:

##### start text #####
ACTION=="add",           GOTO="Insert_eToken"
ACTION=="remove",        GOTO="Remove_eToken"
GOTO="hotplug_end"
LABEL="Insert_eToken"

### eToken PRO 32K, 64K
BUS=="usb", SYSFS{product}=="eToken Pro [0-9][0-9][0-9][0-9]", SYSFS{manufacturer}=="AKS", SYMLINK="eTokenPro", ENV{DEVICE}="eTokenPro", RUN="/etc/hotplug.d/usb/etoken.hotplug add /dev/eTokenPro"
### eToken NG-OTP(new versions); NG-Flash
BUS=="usb", SYSFS{product}=="Token [0-9].[0-9][0-9].[0-9].[0-9] [0-9].[0-9].[0-9][0-9][0-9]", SYSFS{manufacturer}=="Aladdin Knowledge Systems Ltd.", SYMLINK="eTokenNG", ENV{DEVICE}="eTokenNG", RUN="/etc/hotplug.d/usb/etoken.hotplug add /dev/eTokenNG"

### eToken NG-OTP(old versions)
BUS=="usb", SYSFS{product}=="eToken NG-OTP V[0-9].[0-9]", SYSFS{manufacturer}=="Aladdin Knowledge Systems Ltd.", SYMLINK="eTokenNG", ENV{DEVICE}="eTokenNG", RUN="/etc/hotplug.d/usb/etoken.hotplug add /dev/eTokenNG"
LABEL="Remove_eToken"

### eToken PRO 32K, 64K
BUS=="usb", SYSFS{product}=="eToken Pro [0-9][0-9][0-9][0-9]", SYSFS{manufacturer}=="AKS", SYMLINK="eTokenPro", ENV{DEVICE}="eTokenPro", RUN="/etc/hotplug.d/usb/etoken.hotplug remove /dev/eTokenPro"

### eToken NG-OTP(new versions); NG-Flash
BUS=="usb", SYSFS{product}=="Token [0-9].[0-9][0-9].[0-9].[0-9] [0-9].[0-9].[0-9][0-9][0-9]", SYSFS{manufacturer}=="Aladdin Knowledge Systems Ltd.", SYMLINK="eTokenNG", ENV{DEVICE}="eTokenNG", RUN="/etc/hotplug.d/usb/etoken.hotplug remove /dev/eTokenNG"

### eToken NG-OTP(old versions)
BUS=="usb", SYSFS{product}=="eToken NG-OTP V[0-9].[0-9]", SYSFS{manufacturer}=="Aladdin Knowledge Systems Ltd.", SYMLINK="eTokenNG", ENV{DEVICE}="eTokenNG", RUN="/etc/hotplug.d/usb/etoken.hotplug remove /dev/eTokenNG"

LABEL="hotplug_end"
##### end text #####


------------------------------------------------------------
Test
------------------------------------------------------------

To see your eToken contents:
# /usr/local/bin/etckdump --slot=0

To see your eToken contents when you know its PIN code (1234567890 is the default eToken password):
# /usr/local/bin/etckdump --slot=0 --pin=1234567890

To initialize a new token and set the user PIN to 1234:
# /usr/local/bin/etckinit 0 1234567890 1234

Output:
# Get all the occupied slots
# Load Pkcs#11 Dll and get Function list.
# Open session
# Logging to eToken as SO with format password
# Close session
# Initialize token with format password
# Open session
# Logging in to eToken as SO with password - 1234567890
# Initialize USER PIN to 1234
# Logout
# Logging in to eToken as USER with - 1234 
# Close session

;)

---

