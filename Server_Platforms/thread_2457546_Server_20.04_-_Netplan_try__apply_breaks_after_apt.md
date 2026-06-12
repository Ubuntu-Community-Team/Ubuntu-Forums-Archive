---
title: "Server 20.04 - Netplan try / apply breaks after apt update"
date: 2021-02-04
forum: Server Platforms
---

### Post by zeuswoz99 on 2021-02-04
[COLOR=#242729][FONT=Arial]I've got a strange issue that I only get on a vm and not on any baremetal installs.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]After doing a clean install and configuring the network, netplan works as expected. However after running atp update, netplan breaks. The error I get is below

[/FONT][/COLOR]
```
root@wozdc01:/home/zeus# netplan try
Job for netplan-wpa-wlp4s0.service canceled.

An error occurred: Command '['systemctl', 'stop', 'systemd-networkd.service', 'netplan-wpa-*.service']' returned non-zero exit status 1.

Reverting.
Job for netplan-wpa-wlp4s0.service canceled.
Traceback (most recent call last):
  File "/usr/share/netplan/netplan/cli/commands/try_command.py", line 84, in command_try
    NetplanApply().command_apply(run_generate=True, sync=True, exit_on_error=False)
  File "/usr/share/netplan/netplan/cli/commands/apply.py", line 160, in command_apply
    utils.systemctl_networkd('stop', sync=sync, extra_services=wpa_services)
  File "/usr/share/netplan/netplan/cli/utils.py", line 125, in systemctl_networkd
    subprocess.check_call(command)
  File "/usr/lib/python3.8/subprocess.py", line 364, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['systemctl', 'stop', 'systemd-networkd.service', 'netplan-wpa-*.service']' returned non-zero exit status 1.

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/sbin/netplan", line 23, in <module>
    netplan.main()
  File "/usr/share/netplan/netplan/cli/core.py", line 50, in main
    self.run_command()
  File "/usr/share/netplan/netplan/cli/utils.py", line 257, in run_command
    self.func()
  File "/usr/share/netplan/netplan/cli/commands/try_command.py", line 66, in run
    self.run_command()
  File "/usr/share/netplan/netplan/cli/utils.py", line 257, in run_command
    self.func()
  File "/usr/share/netplan/netplan/cli/commands/try_command.py", line 95, in command_try
    self.revert()
  File "/usr/share/netplan/netplan/cli/commands/try_command.py", line 118, in revert
    NetplanApply().command_apply(run_generate=False, sync=True, exit_on_error=False)
  File "/usr/share/netplan/netplan/cli/commands/apply.py", line 160, in command_apply
    utils.systemctl_networkd('stop', sync=sync, extra_services=wpa_services)
  File "/usr/share/netplan/netplan/cli/utils.py", line 125, in systemctl_networkd
    subprocess.check_call(command)
  File "/usr/lib/python3.8/subprocess.py", line 364, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['systemctl', 'stop', 'systemd-networkd.service', 'netplan-wpa-*.service']' returned non-zero exit status 1.


```

[COLOR=#242729][FONT=Arial]This error happens regardless if any changes have been made to yaml files.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Below is the list of packages that apt updated

[/FONT][/COLOR]
```
accountsservice alsa-ucm-conf apparmor apport apt apt-utils base-files bash bcache-tools bind9-dnsutils
  bind9-host bind9-libs bolt bsdutils busybox-initramfs busybox-static ca-certificates command-not-found
  cryptsetup cryptsetup-bin cryptsetup-initramfs cryptsetup-run curl dbus dbus-user-session distro-info-data fdisk
  finalrd fwupd fwupd-signed gcc-10-base gir1.2-glib-2.0 gir1.2-packagekitglib-1.0 glib-networking
  glib-networking-common glib-networking-services grub-common grub-efi-amd64 grub-efi-amd64-bin
  grub-efi-amd64-signed grub2-common initramfs-tools initramfs-tools-bin initramfs-tools-core intel-microcode
  krb5-locales landscape-common language-selector-common less libaccountsservice0 libapparmor1 libapt-pkg6.0
  libasound2 libasound2-data libblkid1 libbrotli1 libc-bin libc6 libcryptsetup12 libcurl3-gnutls libcurl4
  libdbus-1-3 libdns-export1109 libdrm-common libdrm2 libefiboot1 libefivar1 libfdisk1 libfreetype6 libfwupd2
  libfwupdplugin1 libgcc-s1 libgirepository-1.0-1 libglib2.0-0 libglib2.0-bin libglib2.0-data libgnutls30
  libgssapi-krb5-2 libisc-export1105 libjson-c4 libk5crypto3 libkrb5-3 libkrb5support0 libldap-2.4-2
  libldap-common liblzma5 libmaxminddb0 libmount1 libnetplan0 libnss-systemd libp11-kit0 libpackagekit-glib2-18
  libpam-modules libpam-modules-bin libpam-runtime libpam-systemd libpam0g libparted2 libperl5.30 libplymouth5
  libproxy1v5 libpython3.8 libpython3.8-minimal libpython3.8-stdlib libseccomp2 libsmartcols1 libsqlite3-0
  libssh-4 libssl1.1 libstdc++6 libsystemd0 libudev1 libuuid1 libuv1 libx11-6 libx11-data linux-base
  linux-firmware linux-generic linux-headers-generic linux-image-generic locales login lshw lsof mdadm mount
  netplan.io open-iscsi open-vm-tools openssh-client openssh-server openssh-sftp-server openssl packagekit
  packagekit-tools parted passwd perl perl-base perl-modules-5.30 plymouth plymouth-theme-ubuntu-text
  python-apt-common python3-apport python3-apt python3-commandnotfound python3-cryptography python3-distupgrade
  python3-distutils python3-gdbm python3-lib2to3 python3-problem-report python3-software-properties
  python3-update-manager python3-urllib3 python3.8 python3.8-minimal rsyslog shim shim-signed snapd
  software-properties-common sosreport strace sudo systemd systemd-sysv systemd-timesyncd tar thermald tmux tzdata
  ubuntu-minimal ubuntu-release-upgrader-core ubuntu-server ubuntu-standard udev unattended-upgrades
  update-manager-core update-notifier-common util-linux uuid-runtime wireless-regdb xz-utils zlib1g

```

[COLOR=#242729][FONT=Arial]I have done a clean install several times and recreated the vm from scratch. The host has also been rebooted.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any ideas?[/FONT][/COLOR]

---

### Post by TheFu on 2021-02-04
That looks more like an OS install or distro replacement than a weekly patch session.  
Servers don't have wifi, BTW.  They use wired connections.  And the hostOS network setup would be useful too.

Perhaps if you posted the netplan file(s), using code tags, someone can help? There are at least 10 examples in these forums for simple netplan files.

I'm not seeing any issues with my 20.04 netplan config running in a KVM VM, with a bridged connection under the Ubuntu host.

---

### Post by zeuswoz99 on 2021-02-07
The error happens even if there are no changes to a netplan file that worked before any updates were applied.

So far I've tracked the issue to one of the following packages. Although the error is different, it does indicate that one of these affects the way the netplan scripts works.

```
accountsservice alsa-ucm-conf apparmor apport apt apt-utils base-files bash bcache-tools bind9-dnsutils
  bind9-host bind9-libs bolt bsdutils busybox-initramfs busybox-static ca-certificates command-not-found
  cryptsetup cryptsetup-bin cryptsetup-initramfs cryptsetup-run curl dbus dbus-user-session distro-info-data fdisk
  finalrd fwupd fwupd-signed gcc-10-base gir1.2-glib-2.0 gir1.2-packagekitglib-1.0 glib-networking
  glib-networking-common glib-networking-services grub-common grub-efi-amd64 grub-efi-amd64-bin
  grub-efi-amd64-signed grub2-common initramfs-tools initramfs-tools-bin initramfs-tools-core intel-microcode
  krb5-locales landscape-common language-selector-common less libaccountsservice0 libapparmor1 libapt-pkg6.0
  libasound2 libasound2-data libblkid1 libbrotli1 libc-bin libc6 libcryptsetup12 libcurl3-gnutls libcurl4
  libdbus-1-3 libdns-export1109 libdrm-common libdrm2 libefiboot1 libefivar1 libfdisk1 libfreetype6 libfwupd2
  libfwupdplugin1 libgcc-s1 libgirepository-1.0-1 libglib2.0-0 libglib2.0-bin libglib2.0-data libgnutls30
  libgssapi-krb5-2 libisc-export1105 libjson-c4 libk5crypto3 libkrb5-3 libkrb5support0 libldap-2.4-2
  libldap-common liblzma5 libmaxminddb0 libmount1 libnetplan0 libnss-systemd libp11-kit0 libpackagekit-glib2-18
  libpam-modules libpam-modules-bin libpam-runtime libpam-systemd libpam0g libparted2 libperl5.30 libplymouth5
  libproxy1v5
```

As for the comment about "servers don't have wifi", that all depends on what the server is going to be used for (e.g. a router).

---

### Post by kevdog on 2021-02-09
Hi -- just another suggestion you might want to try -- its a little bit of a change.  After running a bunch of servers on Arch, I've realized netplan is just a frontend for systemd-networkd.  I honestly have no idea why netplan exists, and I say this truthfully since its just about as easy to configure systemd-networkd directly as it is using netplan -- so I really dont understand the "value-add" of netplan since ease of use is not one of them.  On my Ubuntu servers I use either netplan or systemd-networkd directly (netplan for the older servers and systemd-networkd) for the newer servers.

For example if you look at a typical netplan file:

```

network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s5:
     dhcp4: no
     addresses: [10.0.1.95/24]
     gateway4: 10.0.1.1
     nameservers:
       addresses: [10.0.1.1,1.1.1.1]

```

The renderer line -- it calls systemd-networkd.

A typical systemd-networkd config file (config files can be separate and are located within the /etc/systemd/network directory) could be:

```

Name=eth0

[Network]
DHCP=ipv4
DNS=10.0.1.1
IPForward=ipv4

[DHCP]
UseDNS=true

```

You can see the structures are very similar, netplan uses yaml where as systemd-netword uses various sections.

You might just try configuring systemd-networkd directly and then just restart the systemd-networkd service.  
Just a thought.

---

### Post by #&amp;thj^% on 2021-02-09
Try kevdog's suggestion first if that still gives you grief, then see if the following helps.

I'm also using WiFi.
My edit to "/etc/netplan/50-cloud-init.yaml"is simalar to this:

YAML files are very sensitive about spaces, indention and alignment. Don’t use tabs, use 4 (or 2, whichever is already used in the YAML file) spaces instead where you see an indention.

Basically, you’ll have to add the following lines with the access point name (SSID) and its password (usually) in quotes:
```

wifis:
    wlan0:
        dhcp4: true
        optional: true
        access-points:
            "SSID_name":
                password: "WiFi_password"
```

Again, keep the alignment as I have shown or else YAML file won’t be parsed and it will throw an error.

Your complete configuration file may look like this:
```

# This file is generated from information provided by the datasource. Changes
# to it will not persist across an instance reboot. To disable cloud-init's
# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        eth0:
            dhcp4: true
            optional: true
    version: 2
    wifis:
        wlan0:
            dhcp4: true
            optional: true
            access-points:
                "SSID_name":
                    password: "WiFi_password"
```

I find it strange that despite the message that changes will not persist across an instance reboot, it still works.

Anyway, generate the configuration using this command:
```

sudo netplan generate
```

And now apply this:

```
sudo netplan apply
```

If you are lucky, you should have network connected. Try to ping a website or run apt update command.

However, things may not go as smooth and you may see some errors. Try some extra steps if that’s the case.
Possible troubleshooting

It is possible that when you use the netplan apply command, you see an error in the output that reads something like this:
```

Failed to start netplan-wpa-wlan0.service: Unit netplan-wpa-wlan0.service not found.
Traceback (most recent call last):
  File "/usr/sbin/netplan", line 23, in <module>
    netplan.main()
  File "/usr/share/netplan/netplan/cli/core.py", line 50, in main
    self.run_command()
  File "/usr/share/netplan/netplan/cli/utils.py", line 179, in run_command
    self.func()
  File "/usr/share/netplan/netplan/cli/commands/apply.py", line 46, in run
    self.run_command()
  File "/usr/share/netplan/netplan/cli/utils.py", line 179, in run_command
    self.func()
  File "/usr/share/netplan/netplan/cli/commands/apply.py", line 173, in command_apply
    utils.systemctl_networkd('start', sync=sync, extra_services=netplan_wpa)
  File "/usr/share/netplan/netplan/cli/utils.py", line 86, in systemctl_networkd
    subprocess.check_call(command)
  File "/usr/lib/python3.8/subprocess.py", line 364, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['systemctl', 'start', '--no-block', 'systemd-networkd.service', 'netplan-wpa-wlan0.service']' returned non-zero exit status 5.
```

**It is possible that wpa_supplicant service is not running. Run this command:**
```

sudo systemctl start wpa_supplicant
```

Run netplan apply once again. If it fixes the issue well and good. Otherwise, shutdown your Ubuntu system using:
```

shutdown now
```

Start your Ubuntu system again, log in and generate and apply netplan once again:
```

sudo netplan generate
sudo netplan apply
```

It may show warning (instead of error) now. It is warning and not an error. I checked the running systemd services and found that netplan-wpa-wlan0.service was already running. Probably it showed the warning because it was already running and ‘netplan apply’ updated the config file (even without any changes).

Warning: The unit file, source configuration file or drop-ins of netplan-wpa-wlan0.service changed on disk. Run 'systemctl daemon-reload' to reload units.

It is not critical and you may check that the internet is probably working already by running apt update.

I hope that helps.

---

### Post by rsteinmetz70112 on 2021-02-09
I have one server that I recently upgraded to 20.04 and netplan is not working. I was able to get the server working and someday I'll comeback and try to get netplan working. I wanted to post just to let you know you're not alone.

---

