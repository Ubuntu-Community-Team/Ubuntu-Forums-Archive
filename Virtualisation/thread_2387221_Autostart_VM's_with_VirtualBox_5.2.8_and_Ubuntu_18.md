---
title: "Autostart VM's with VirtualBox 5.2.8 and Ubuntu 18.04"
date: 2018-03-16
forum: Virtualisation
---

### Post by antonto on 2018-03-16
Hi All! 
I faced up with trouble with autostart VM on Ubuntu 18.04 and look like I've got the solution:

VirtualBox installed from repos. Ver 5.2.8
Ubuntu 18.04 beta

First point: The method described in official VirtualBox [manuals]("https://www.virtualbox.org/manual/ch09.html#autostart") for run VM's at start is not working. I can't understand why, but looks like the Ubuntu deb-package does not include **[COLOR=#303336][FONT=inherit]vboxautostart[/FONT][/COLOR][COLOR=#303336][FONT=inherit]-[/FONT][/COLOR][COLOR=#303336][FONT=inherit]service[/FONT][/COLOR]**
Ok, I've wrote my own, as described here: [https://ubuntuforums.org/showthread.php?t=2326419](https://ubuntuforums.org/showthread.php?t=2326419)
But it also has not worked properly. I've got the error at system start: 
**/etc/systemd/system/vboxauto.service:** ```

&#1084;&#1072;&#1088; 16 11:27:28 atx systemd[1]: Starting Autostart VirtualBox machines...
&#1084;&#1072;&#1088; 16 11:27:28 atx systemd[1]: Started Autostart VirtualBox machines.
&#1084;&#1072;&#1088; 16 11:27:28 atx root[1164]: WARNING: The character device /dev/vboxdrv does not exist.
&#1084;&#1072;&#1088; 16 11:27:28 atx root[1164]:          Please install the virtualbox-dkms package and the appropriate
&#1084;&#1072;&#1088; 16 11:27:28 atx root[1164]:          headers, most likely linux-headers-generic.
&#1084;&#1072;&#1088; 16 11:27:28 atx root[1164]: 
&#1084;&#1072;&#1088; 16 11:27:28 atx root[1164]:          You will not be able to start VMs until this problem is fixed.
&#1084;&#1072;&#1088; 16 11:27:29 atx root[1164]: VBoxHeadless: Error -1908 in suplibOsInit!
&#1084;&#1072;&#1088; 16 11:27:29 atx root[1164]: VBoxHeadless: Kernel driver not installed
&#1084;&#1072;&#1088; 16 11:27:29 atx root[1164]: 
&#1084;&#1072;&#1088; 16 11:27:29 atx root[1164]: VBoxHeadless: Tip! Make sure the kernel module is loaded. It may also help to reinstall VirtualBox.

```

If I run service manually it working fine:

```
sudo systemctl start vboxauto.service
```

Looks like I've tried  to start VM before **vboxdrv **loaded. So I inspect the order of loaded services and found that virtualbox.service run towards the end of the list. So all, that we need is wait for virtualbox.service and then start the VM!
The correct service file here:
```

[Unit]
Description=Autostart VirtualBox machines
After=virtualbox.service

[Service]
Type=oneshot
RemainAfterExit=yes

ExecStart=/usr/bin/vbox.sh start
ExecStop=/usr/bin/vbox.sh stop

[Install]
WantedBy=multi-user.target

```

I'm use additional script /usr/bin/vbox.sh for graceful VM shutdown and other small hacks, but you can start and stop VM directly:

```

...
ExecStart=/usr/bin/VBoxHeadless --startvm "virtualserver"
ExecStop=/usr/bin/VBoxManage controlvm "virtualserver" poweroff
...

```

**tip:** You can see all running services, orders and timings with command **systemd-analyze plot >temp.xml **and then open tmp.xml with any web-browser.

**vbox.sh:**
```
vm="virtualserver"
# how long in seconds we will wait for gracefull shutdown before force poweroff
timeout=20

#logger "$0 running with [$*]..."

start() {
  # we place EXEC for hack. We need to hide VBoxHeadless PID from systemd. In the other case, in the stop() we must wait until VBoxHeadless exit, but we do not need it.
  exec VBoxHeadless --startvm "$vm" 2>&1 | logger & 
  exit $?
}

stop() {
  echo -n "Try to stop VM..."
  vboxmanage controlvm "$vm" acpipowerbutton
  #vboxmanage controlvm "$vm" savestate
  # next, we need to wait until VM is stopped
  for i in `seq 1 $timeout`;
  do
    if ! VBoxManage list runningvms | grep $vm >/dev/null; then
       echo "done!"
       #sleep 1      
       exit 0
    fi
    echo -n .
    sleep 1;
  done    
  echo "save state failed. Forced poweroff."
  vboxmanage controlvm "$vm" poweroff
  sleep 1 
  exit 0
}

status() {
  echo "Running machines:"
  vboxmanage list runningvms     
}

case $1 in
  start|stop|status) "$1" 
   ;;
  *) echo "Usage: $0 [sart|stop|status]"
     exit 1
   ;;
esac

```

---

### Post by blazeag on 2018-08-10
Mega-thank-you!

---

