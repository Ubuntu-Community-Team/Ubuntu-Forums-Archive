---
title: "Erase a partition without entering a password? Really???"
date: 2010-01-02
forum: Security
---

### Post by hhh on 2010-01-02
I've installed Karmic after having used Jaunty in the past and it's working great, but I have a couple of security questions...

I opened the Disc Utility (Palimpsest) under System>Administration and was amazed that it looks like it will let me delete partitions on my hard drive, and without even asking for a password. This seems like an enormous security oversight, what am I missing here? Is there a bug filed for this?

Also related, why does Ubuntu allow a user to disable startup applications without requiring a password?

---

### Post by mbruins on 2010-01-02
> Also related, why does Ubuntu allow a user to disable startup applications without requiring a password?I'm not sure why not. The changes will only affect the current user. And can be re-enabled by that same user.

---

### Post by drs305 on 2010-01-02
> **hhh said:**
> I've installed Karmic after having used Jaunty in the past and it's working great, but I have a couple of security questions...

I opened the Disc Utility (Palimpsest) under System>Administration and was amazed that it looks like it will let me delete partitions on my hard drive, and without even asking for a password. This seems like an enormous security oversight, what am I missing here? Is there a bug filed for this?

To access Disk Utility/Palimpsest via the System > Admin command you have to enter your admin password, so in effect you are running it with adminstrative rights. That gives you the opportunity to do what you will with the partitions, including trashing the system.  ;-)

---

### Post by hhh on 2010-01-02
I know they can be enabled by the same user, that's not the point. If you've left your Ubuntu desktop for a second and someone knows the basics, they can switch off, say, Network Manager and the next time you reboot you'll be going "What the...?"

---

### Post by mbruins on 2010-01-02
> I know they can be enabled by the same user, that's not the point. If you've left your Ubuntu desktop for a second and someone knows the basics, they can switch off, say, Network Manager and the next time you reboot you'll be going "What the...?"

I've you really suspect that someone would do that. You could aways lock your screen when leaving System > Lock screen. When you're back you can unlock the screen by entering your password You could also remove the Startup "option" in the user menu.

---

### Post by hhh on 2010-01-02
I'm speaking hypothetically, my Ubuntu install is at home and I live alone. Still, I've removed both menu items to make sure I don't accidentally do anything forgetful/regretful.

I just rebooted and I was correct, the Disc Utility fires right up from System>Administration without requiring any password and I can select a partition and click "Delete" and only receive a warning about it. That seems ridiculously insecure to me. Again, what am I missing?

---

### Post by iponeverything on 2010-01-02
You have to enter a password to start the partition editor in the first place, I don't see your point in requiring that it be entered again to do something in it.

As for changing setting and altering startup programs for user who already entered his password to log to me also seems kind of silly, would you also want the system to prompt for a password before allowing the the user to delete items from his Desktop or from his own home directory?

---

### Post by iponeverything on 2010-01-02
> **hhh said:**
> I'm speaking hypothetically, my Ubuntu install is at home and I live alone. Still, I've removed both menu items to make sure I don't accidentally do anything forgetful/regretful.

I just rebooted and I was correct, the Disc Utility fires right up from System>Administration without requiring any password and I can select a partition and click "Delete" and only receive a warning about it. That seems ridiculously insecure to me. Again, what am I missing?

I am thinking that maybe you clicked on "remember authorization" some time in the past when you used the utility.

---

### Post by hhh on 2010-01-02
> **iponeverything said:**
> You have to enter a password to start the partition editor in the first place...

No, you don't. Try it from a reboot, it lets you right in.

Ubuntu requires a password to sync the clock with an internet server, but not for disc management?

---

### Post by hhh on 2010-01-02
> **iponeverything said:**
> I am thinking that maybe you clicked on "remember authorization" some time in the past when you used the utility.
I don't think so, the install is only a couple of days old. I'm looking for stored passwords now but I'm not finding where they're stored.

Edit- got it, I forgot it's under "Accessories" and not under "Administration", which makes no sense either. The only password I have is my log-in, which I have set to allow me to boot without having to enter a password. I just changed that, but was still able to access the disc utility without entering my password again. Like I said, I have to enter a password to set the system clock but not to delete the disc that the install resides on? Does that make any sense?

---

### Post by sisco311 on 2010-01-02
> **hhh said:**
> I don't think so, the install is only a couple of days old. I'm looking for stored passwords now but I'm not finding where they're stored.

Edit- got it, I forgot it's under "Accessories" and not under "Administration", which makes no sense either. The only password I have is my log-in, which I have set to allow me to boot without having to enter a password. I just changed that, but was still able to access the disc utility without entering my password again. Like I said, I have to enter a password to set the system clock but not to delete the disc that the install resides on? Does that make any sense?

Did you actually delete a partition?

palimpsest uses PolicyKit to elevate privileges. You should be prompted for a password after the warning message.

---

### Post by hhh on 2010-01-02
@sisco311, no, I considered testing with my swap partition but decided to post here first. Yours was the answer I was looking for. Thanks!

-edit- looking for a way to mark this thread "Solved". I guess a moderator has to do it?

---

### Post by CharlesA on 2010-01-02
Thread tools > Mark as solved. :)

---

### Post by hhh on 2010-01-02
> **CharlesA said:**
> Thread tools > Mark as solved. :)
Thanks Charles!

---

### Post by W.McL on 2010-01-05
I can confirm the dangerous bahavior of palimpsest. After I upgraded to Karmic, palimpsest started bothering me with false positives on bad sectors. After I confirm the warning message that pops up after login, There is a warning icon in the notification area. When I now start palimpsest (no matter if from the menu, or from the warning icon), I can delete and create partitions without being asked for any legitimation.

I filed this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/503568](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/503568)

---

### Post by sisco311 on 2010-01-05
> **W.McL said:**
> I can confirm the dangerous bahavior of palimpsest. After I upgraded to Karmic, palimpsest started bothering me with false positives on bad sectors. After I confirm the warning message that pops up after login, There is a warning icon in the notification area. When I now start palimpsest (no matter if from the menu, or from the warning icon), I can delete and create partitions without being asked for any legitimation.

I filed this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/503568](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/503568)

Weird...

What's the output of:
```
 pkaction --verbose
```?

---

### Post by W.McL on 2010-01-05
I did not edit any configuration of policykit, however, here's the output of pkaction --verbose:

```
org.freedesktop.devicekit.disks.drive-ata-smart-selftest:
  description:       Run ATA SMART Self Tests
  message:           Authentication is required to run ATA SMART self tests
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin

org.gnome.clockapplet.mechanism.settime:
  description:       Change system time
  message:           Privileges are required to change the system time.
  vendor:            The GNOME Project
  vendor_url:        http://www.gnome.org/
  icon:              gnome-panel-clock
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.freedesktop.devicekit.disks.filesystem-lsof:
  description:       List open files
  message:           Authentication is required to list open files on a mounted file system
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

com.hp.hplip.installplugin:
  description:       Install a plug-in into a Hewlett-Packard printer
  message:           System policy prevents installation of a printer plug-in
  vendor:            Hewlett-Packard Development Company
  vendor_url:        http://hplip.net/
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin

org.freedesktop.devicekit.disks.filesystem-check:
  description:       Check file system on a device
  message:           Authentication is required to check the file system on the device
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.freedesktop.devicekit.disks.drive-ata-smart-retrieve-historical-data:
  description:       Retrieve historical ATA SMART data
  message:           Authentication is required to retrieve historical ATA SMART data
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

com.ubuntu.devicedriver.info:
  description:       Get information about local device drivers
  message:           System policy prevents querying device drivers
  vendor:            Jockey driver manager
  vendor_url:        https://launchpad.net/jockey
  icon:              jockey
  implicit any:      yes
  implicit inactive: yes
  implicit active:   yes

org.debian.apt.add-vendor-key:
  description:       Add a vendor key to the trusted ones
  message:               
  vendor:            Apt Daemon
  vendor_url:        http://launchpad.net/aptdaemon/
  icon:              package-x-generic
  implicit any:      auth_admin
  implicit inactive: auth_admin
  implicit active:   auth_admin_keep

org.freedesktop.devicekit.disks.filesystem-mount:
  description:       Mount a device
  message:           Authentication is required to mount the device
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

com.ubuntu.screenresolution.mechanism.dontzap:
  description:       Change the effect of Ctrl+Alt+Backspace
  message:           Changing the effect of Ctrl+Alt+Backspace requires privileges.
  vendor:            Screen Resolution Extra
  vendor_url:        https://launchpad.net/screen-resolution-extra
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.freedesktop.devicekit.disks.drive-detach:
  description:       Detach a drive
  message:           Authentication is required to detach the drive
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.freedesktop.devicekit.disks.filesystem-unmount-others:
  description:       Unmount a device mounted by another user
  message:           Authentication is required to unmount devices mounted by another user
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin

org.freedesktop.devicekit.disks.linux-md:
  description:       Configure Linux Software RAID
  message:           Authentication is required to configure Linux Software RAID devices
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.freedesktop.devicekit.disks.drive-eject:
  description:       Eject media from a device
  message:           Authentication is required to eject media from the device
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

com.ubuntu.systemservice.setnoproxy:
  description:       Set current global proxy exception
  message:           System policy prevents setting no_proxy settings
  vendor:            SystemService
  vendor_url:        https://launchpad.net/system-service
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.gnome.gconf.defaults.set-system:
  description:       Change GConf system values
  message:           Privileges are required to change GConf system values
  vendor:            The GNOME Project
  vendor_url:        http://www.gnome.org/projects/gconf/
  icon:              gconf-editor
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin

org.debian.apt.change-repository:
  description:       Change software repository
  message:               
  vendor:            Apt Daemon
  vendor_url:        http://launchpad.net/aptdaemon/
  icon:              package-x-generic
  implicit any:      auth_admin
  implicit inactive: auth_admin
  implicit active:   auth_admin_keep

org.freedesktop.network-manager-settings.system.wifi.share.protected:
  description:       Connection sharing via a protected WiFi network
  message:           System policy prevents sharing connections via a protected WiFi network
  vendor:            NetworkManager
  vendor_url:        http://www.gnome.org/projects/NetworkManager
  icon:              nm-icon
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.freedesktop.policykit.grant:
  description:       Grant authorizations to other users
  message:           Authentication is required to grant authorizations to other users
  vendor:            The PolicyKit Project
  vendor_url:        http://hal.freedesktop.org/docs/PolicyKit/
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.debian.apt.install-packages:
  description:       Install packages
  message:           Authentication is required to install software packages
  vendor:            Apt Daemon
  vendor_url:        http://launchpad.net/aptdaemon/
  icon:              package-x-generic
  implicit any:      auth_admin
  implicit inactive: auth_admin
  implicit active:   auth_admin_keep

com.ubuntu.devicedriver.install:
  description:       Install or remove device drivers
  message:           System policy prevents installation/removal of device drivers
  vendor:            Jockey driver manager
  vendor_url:        https://launchpad.net/jockey
  icon:              jockey
  implicit any:      auth_admin
  implicit inactive: auth_admin
  implicit active:   auth_admin_keep

org.freedesktop.devicekit.disks.cancel-job-others:
  description:       Cancel a job initiated by another user
  message:           Authentication is required to cancel a job initiated by another user
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin

org.debian.apt.cancel-foreign:
  description:       Cancel the task of another user
  message:           Authentication is required to cancel the package management taks of another user.
  vendor:            Apt Daemon
  vendor_url:        http://launchpad.net/aptdaemon/
  icon:              package-x-generic
  implicit any:      auth_admin
  implicit inactive: auth_admin
  implicit active:   auth_admin_keep

org.freedesktop.network-manager-settings.system.hostname.modify:
  description:       Modify persistent system hostname
  message:           System policy prevents modification of the persistent system hostname
  vendor:            NetworkManager
  vendor_url:        http://www.gnome.org/projects/NetworkManager
  icon:              nm-icon
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.freedesktop.devicekit.power.hibernate:
  description:       Hibernate the system
  message:           Authentication is required to hibernate the system
  vendor:            The DeviceKit-power Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit-power/
  icon:              system-suspend
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.freedesktop.devicekit.disks.filesystem-check-system-internal:
  description:       Check file system of a system-internal device
  message:           Authentication is required to check the file system on the device
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.debian.apt.remove-vendor-key:
  description:       Remove a trusted vendor key
  message:               
  vendor:            Apt Daemon
  vendor_url:        http://launchpad.net/aptdaemon/
  icon:              package-x-generic
  implicit any:      auth_admin
  implicit inactive: auth_admin
  implicit active:   auth_admin_keep

org.debian.apt.remove-packages:
  description:       Remove packages
  message:           Authentication is required to remove software packages
  vendor:            Apt Daemon
  vendor_url:        http://launchpad.net/aptdaemon/
  icon:              package-x-generic
  implicit any:      auth_admin
  implicit inactive: auth_admin
  implicit active:   auth_admin_keep

org.gnome.gconf.defaults.set-mandatory:
  description:       Change GConf mandatory values
  message:           Privileges are required to change GConf mandatory values
  vendor:            The GNOME Project
  vendor_url:        http://www.gnome.org/projects/gconf/
  icon:              gconf-editor
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin

org.freedesktop.devicekit.disks.drive-ata-smart-refresh:
  description:       Refresh ATA SMART data
  message:           Authentication is required to refresh ATA SMART data
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

com.ubuntu.usbcreator.image:
  description:       
  message:           
  vendor:            USB Creator
  vendor_url:        https://launchpad.net/usb-creator
  icon:              usb-creator-gtk
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.gnome.cpufreqselector:
  description:       Change CPU Frequency scaling
  message:           Privileges are required to change the CPU Frequency scaling.
  vendor:            The GNOME Project
  vendor_url:        http://www.gnome.org/
  icon:              gnome-cpu-frequency-applet
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

com.ubuntu.systemservice.setproxy:
  description:       Set current global proxy
  message:           System policy prevents setting proxy settings
  vendor:            SystemService
  vendor_url:        https://launchpad.net/system-service
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.freedesktop.systemtoolsbackends.self.set:
  description:       Change the user's own account configuration
  message:           System policy requires you to authenticate in order to modify your user account information
  vendor:            
  vendor_url:        
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_self

org.debian.apt.upgrade-packages:
  description:       Upgrade packages
  message:           Authentication is required to upgrade software packages
  vendor:            Apt Daemon
  vendor_url:        http://launchpad.net/aptdaemon/
  icon:              package-x-generic
  implicit any:      auth_admin
  implicit inactive: auth_admin
  implicit active:   auth_admin_keep

org.debian.apt.get-trusted-vendor-keys:
  description:       List keys of trusted vendors
  message:               
  vendor:            Apt Daemon
  vendor_url:        http://launchpad.net/aptdaemon/
  icon:              package-x-generic
  implicit any:      auth_admin
  implicit inactive: auth_admin
  implicit active:   auth_admin_keep

org.debian.apt.upgrade-system:
  description:       Upgrade system
  message:           Authentication is required to upgrade the system
  vendor:            Apt Daemon
  vendor_url:        http://launchpad.net/aptdaemon/
  icon:              package-x-generic
  implicit any:      auth_admin
  implicit inactive: auth_admin
  implicit active:   auth_admin_keep

org.freedesktop.devicekit.power.suspend:
  description:       Suspend the system
  message:           Authentication is required to suspend the system
  vendor:            The DeviceKit-power Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit-power/
  icon:              system-suspend
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.freedesktop.devicekit.power.qos.request-latency-persistent:
  description:       Set a persistent latency setting
  message:           Authentication is required to set a persistent latency setting
  vendor:            The DeviceKit-power Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit-power/
  icon:              system-suspend
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.gnome.clockapplet.mechanism.configurehwclock:
  description:       Configure hardware clock
  message:           Privileges are required to configure the hardware clock.
  vendor:            The GNOME Project
  vendor_url:        http://www.gnome.org/
  icon:              gnome-panel-clock
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.freedesktop.devicekit.disks.filesystem-mount-system-internal:
  description:       Mount a system-internal device
  message:           Authentication is required to mount the device
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

com.ubuntu.devicedriver.check:
  description:       Check for newly available drivers for, and used drivers on this system
  message:           System policy prevents checking driver status
  vendor:            Jockey driver manager
  vendor_url:        https://launchpad.net/jockey
  icon:              jockey
  implicit any:      no
  implicit inactive: yes
  implicit active:   yes

org.freedesktop.network-manager-settings.system.wifi.share.open:
  description:       Connection sharing via an open WiFi network
  message:           System policy prevents sharing connections via an open WiFi network
  vendor:            NetworkManager
  vendor_url:        http://www.gnome.org/projects/NetworkManager
  icon:              nm-icon
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.freedesktop.consolekit.system.restart:
  description:       Restart the system
  message:           System policy prevents restarting the system
  vendor:            
  vendor_url:        
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.freedesktop.devicekit.disks.luks-lock-others:
  description:       Lock an encrypted device unlocked by another user
  message:           Authentication is required to lock an encrypted device unlocked by another user
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin

org.freedesktop.systemtoolsbackends.set:
  description:       Manage system configuration
  message:           System policy prevents modifying the system configuration
  vendor:            
  vendor_url:        
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.freedesktop.consolekit.system.restart-multiple-users:
  description:       Restart the system when multiple users are logged in
  message:           System policy prevents restarting the system when other users are logged in
  vendor:            
  vendor_url:        
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.debian.apt.install-file:
  description:       Install package file
  message:           Authentication is required to install a local package file.
  vendor:            Apt Daemon
  vendor_url:        http://launchpad.net/aptdaemon/
  icon:              package-x-generic
  implicit any:      auth_admin
  implicit inactive: auth_admin
  implicit active:   auth_admin_keep

org.freedesktop.policykit.revoke:
  description:       Revoke authorizations from other users
  message:           Authentication is required to revoke authorizations other users
  vendor:            The PolicyKit Project
  vendor_url:        http://hal.freedesktop.org/docs/PolicyKit/
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.freedesktop.devicekit.power.qos.cancel-request:
  description:       Cancel a latency request
  message:           Authentication is required to cancel a latency request
  vendor:            The DeviceKit-power Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit-power/
  icon:              system-suspend
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin

org.debian.apt.update-cache:
  description:       Update package information
  message:           Authentication is required to query the software repositories for installable packages
  vendor:            Apt Daemon
  vendor_url:        http://launchpad.net/aptdaemon/
  icon:              package-x-generic
  implicit any:      auth_admin
  implicit inactive: auth_admin
  implicit active:   auth_admin_keep

org.freedesktop.devicekit.power.qos.set-minimum-latency:
  description:       Set administrator settings for latency control
  message:           Authentication is required to set administrator settings for latency control
  vendor:            The DeviceKit-power Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit-power/
  icon:              system-suspend
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin

org.freedesktop.policykit.read:
  description:       Read authorizations of other users
  message:           Authentication is required to read authorizations of other users
  vendor:            The PolicyKit Project
  vendor_url:        http://hal.freedesktop.org/docs/PolicyKit/
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.freedesktop.devicekit.disks.luks-unlock:
  description:       Unlock an encrypted device
  message:           Authentication is required to unlock an encrypted device
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.freedesktop.devicekit.disks.drive-set-spindown:
  description:       Set drive spindown timeout
  message:           Authentication is required to configure drive spindown timeout
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.freedesktop.network-manager-settings.system.modify:
  description:       Modify system connections
  message:           System policy prevents modification of system settings
  vendor:            NetworkManager
  vendor_url:        http://www.gnome.org/projects/NetworkManager
  icon:              nm-icon
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

com.ubuntu.systemservice.ispkgsystemlocked:
  description:       Check if the package system is locked
  message:           System policy prevents querying package system lock
  vendor:            SystemService
  vendor_url:        https://launchpad.net/system-service
  icon:              
  implicit any:      no
  implicit inactive: yes
  implicit active:   yes

com.ubuntu.systemservice.getproxy:
  description:       Get current global proxy
  message:           System policy prevents querying proxy settings
  vendor:            SystemService
  vendor_url:        https://launchpad.net/system-service
  icon:              
  implicit any:      no
  implicit inactive: yes
  implicit active:   yes

org.gnome.clockapplet.mechanism.settimezone:
  description:       Change system time zone
  message:           Privileges are required to change the system time zone.
  vendor:            The GNOME Project
  vendor_url:        http://www.gnome.org/
  icon:              gnome-panel-clock
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_self_keep

org.gnome.displaymanager.settings.write:
  description:       
  message:           
  vendor:            The GNOME Project
  vendor_url:        http://www.gnome.org/
  icon:              gdm
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

com.ubuntu.usbcreator.bootloader:
  description:       
  message:           
  vendor:            USB Creator
  vendor_url:        https://launchpad.net/usb-creator
  icon:              usb-creator-gtk
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

com.ubuntu.systemservice.getkeyboard:
  description:       Get current global keyboard
  message:           System policy prevents querying keyboard settings
  vendor:            SystemService
  vendor_url:        https://launchpad.net/system-service
  icon:              
  implicit any:      no
  implicit inactive: yes
  implicit active:   yes

org.freedesktop.devicekit.disks.change:
  description:       Modify a device
  message:           Authentication is required to modify the device
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

com.ubuntu.systemservice.setkeyboard:
  description:       Set current global keyboard
  message:           System policy prevents setting global keyboard settings
  vendor:            SystemService
  vendor_url:        https://launchpad.net/system-service
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

com.ubuntu.devicedriver.update:
  description:       Query local and remote driver databases for updated drivers for the system
  message:           System policy prevents querying driver databases for updates
  vendor:            Jockey driver manager
  vendor_url:        https://launchpad.net/jockey
  icon:              jockey
  implicit any:      no
  implicit inactive: yes
  implicit active:   yes

org.freedesktop.devicekit.power.qos.request-latency:
  description:       Set the required latency of an application
  message:           Authentication is required to set the required latency of an application
  vendor:            The DeviceKit-power Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit-power/
  icon:              system-suspend
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

com.ubuntu.usbcreator.mount:
  description:       
  message:           
  vendor:            USB Creator
  vendor_url:        https://launchpad.net/usb-creator
  icon:              usb-creator-gtk
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.freedesktop.devicekit.disks.change-system-internal:
  description:       Modify a system-internal device
  message:           Authentication is required to modify the device
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.freedesktop.consolekit.system.stop:
  description:       Stop the system
  message:           System policy prevents stopping the system
  vendor:            
  vendor_url:        
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.freedesktop.policykit.modify-defaults:
  description:       Modify defaults for implicit authorizations
  message:           Authentication is required to modify the defaults for implicit authorizations
  vendor:            The PolicyKit Project
  vendor_url:        http://hal.freedesktop.org/docs/PolicyKit/
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.freedesktop.devicekit.disks.filesystem-lsof-system-internal:
  description:       List open files on a system-internal device
  message:           Authentication is required to list open files on a mounted file system
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

org.freedesktop.policykit.exec:
  description:       Run programs as another user
  message:           Authentication is required to run a program as another user
  vendor:            The PolicyKit Project
  vendor_url:        http://hal.freedesktop.org/docs/PolicyKit/
  icon:              
  implicit any:      auth_admin
  implicit inactive: auth_admin
  implicit active:   auth_admin

com.ubuntu.usbcreator.format:
  description:       
  message:           
  vendor:            USB Creator
  vendor_url:        https://launchpad.net/usb-creator
  icon:              usb-creator-gtk
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.freedesktop.devicekit.disks.inhibit-polling:
  description:       Inhibit media detection
  message:           Authentication is required to inhibit media detection
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  implicit active:   yes

org.freedesktop.consolekit.system.stop-multiple-users:
  description:       Stop the system when multiple users are logged in
  message:           System policy prevents stopping the system when other users are logged in
  vendor:            
  vendor_url:        
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

com.ubuntu.screenresolution.mechanism.configure:
  description:       Change Screen Resolution Configuration
  message:           Changing the Screen Resolution configuration requires privileges.
  vendor:            Screen Resolution Extra
  vendor_url:        https://launchpad.net/screen-resolution-extra
  icon:              
  implicit any:      no
  implicit inactive: no
  implicit active:   auth_admin_keep

```

---

### Post by sisco311 on 2010-01-05
```
...
org.freedesktop.devicekit.disks.change:
  description:       Modify a device
  message:           Authentication is required to modify the device
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  **implicit active:   yes**
...
org.freedesktop.devicekit.disks.change-system-internal:
  description:       Modify a system-internal device
  message:           Authentication is required to modify the device
  vendor:            The DeviceKit Project
  vendor_url:        http://hal.freedesktop.org/docs/DeviceKit/
  icon:              drive-removable-media
  implicit any:      no
  implicit inactive: no
  **implicit active:   auth_admin_keep**

```

You are allowed to change (delete/create a partition on) an external disk without password authentication, but you should be prompted for a password if you try to change an internal disk.

[http://hal.freedesktop.org/docs/DeviceKit-disks/Device.html]("http://hal.freedesktop.org/docs/DeviceKit-disks/Device.html")

You can change this behavior by editing the */usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy* file:

```

...
  <action id="org.freedesktop.devicekit.disks.change">
    <description>Modify a device</description>
    <description xml:lang="da">Modificér en enhed</description>
    <description xml:lang="de">Gerät ändern</description>
    <message>Authentication is required to modify the device</message>
    <message xml:lang="da">Autorisering er påkrævet for at ændre en enhed</message>
    <message xml:lang="de">Zugriffsrechte werden benötigt um das Gerät zu ändern</message>
    <defaults>
      <allow_any>no</allow_any>
      <allow_inactive>no</allow_inactive>
      <allow_active>**auth_admin_keep**</allow_active>
    </defaults>
  </action>
...

```

---

### Post by W.McL on 2010-01-05
OK, that's an acceptable behavior. Should have found that out myself, but didn't really want to test it on my only internal device.

Tested, asks for password. No bug. Thank you.

---

