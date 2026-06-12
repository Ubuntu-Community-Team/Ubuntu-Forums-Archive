---
title: "apparmor with chromium"
date: 2010-09-12
forum: Security
---

### Post by bone2006 on 2010-09-12
I wanted to use apparmor with chromium with a profile that was already created and wanted to make sure I did it correctly.

I went to this site
[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/)

and downloaded usr.lib.chromium-browser.chromium-browser
I placed the file in /etc/apparmor.d

Then I ran the command
$sudo enforce usr.lib.chromium-browser.chromium-browser

Status shows
125 profiles are loaded.
13 profiles are in enforce mode.
   /sbin/dhclient3
   /usr/bin/evince
   /usr/bin/evince-previewer
   /usr/bin/evince-thumbnailer
   /usr/bin/freshclam
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/chromium-browser/chromium-browser
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/cupsd
   /usr/sbin/mysqld-akonadi
   /usr/sbin/tcpdump
   /usr/share/gdm/guest-session/Xsession

Looks like it worked alright, but I thought firefox would be there by default as well?  Just want to make sure I'm doing it right for profiles that are already created.  I was going to do transmission next

---

### Post by OpSecShellshock on 2010-09-12
I don't believe that the Firefox profile is enforced (or possibly even active) by default. Thing is, Firefox can be customized in so many ways that there isn't really a good, standard level of protection that would suit a majority of people's needs out of the box. The good news is, that means we get to play with it!

---

### Post by bodhi.zazen on 2010-09-12
That is correct.

For firefox,

```
sudo aa-enforce firefox
```

There is a profile , disabled by default.

---

### Post by bone2006 on 2010-09-12
Thanks so much for the help/response
A quick question, is there any way of testing it?  I was reading that you shouldn't be able to print to pdf with apparmor and your browser, which I just tested chrominum and I was able to print to pdf anywhere I wanted.  
Apparmor is pretty new to me, so I am not that familiar with the profile, which maybe it allows printing to pdf.   If this is the case is there any way of testing apparmor, besides using the program itself?

Thanks again for all the help

---

### Post by bodhi.zazen on 2010-09-12
> **bone2006 said:**
> Thanks so much for the help/response
A quick question, is there any way of testing it?  I was reading that you shouldn't be able to print to pdf with apparmor and your browser, which I just tested chrominum and I was able to print to pdf anywhere I wanted.  
Apparmor is pretty new to me, so I am not that familiar with the profile, which maybe it allows printing to pdf.   If this is the case is there any way of testing apparmor, besides using the program itself?

Thanks again for all the help

Depends on the profile, try to brows you home directory or save a download to ~/.ssh

Watch /var/log/messages

---

### Post by bone2006 on 2010-09-12
I ran a tail -f in one terminal on /var/log/messages
Then opened up chrome that's shown in apparmor_status as being in enforce mode.  
The pdf file was able to save in ~/.ssh and nothing on the messages file showed anything that meant anything to me.   

The file as also able to save in the directory as well.  Does this indicate it's not working?

---

### Post by bodhi.zazen on 2010-09-12
> **bone2006 said:**
> The file as also able to save in the directory as well.  Does this indicate it's not working?

It is "working".

A better question, is it configured the way you wish it to be ? Only you can answer that question. I suggest you read the apparmor sticky and decide for yourself how you wish to modify the configuration, if at all.

---

### Post by rookcifer on 2010-09-12
Here's my Chromium profile that works quite well for me.


```
#include <tunables/global>

/usr/lib/chromium-browser/chromium-browser {
  #include <abstractions/X>
  #include <abstractions/audio>
  #include <abstractions/base>
  #include <abstractions/dbus>
  #include <abstractions/evince>
  #include <abstractions/fonts>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/private-files>
  #include <abstractions/ubuntu-konsole>
  #include <abstractions/user-tmp>

  capability chown,
  capability dac_override,
  capability fsetid,
  capability net_raw,
  capability setgid,
  capability setuid,
  capability sys_admin,
  capability sys_chroot,
  capability sys_ptrace,


  audit deny @{HOME}/.gnome2_private/** mrwlk,
  audit deny @{HOME}/.ssh/** mrwlk,

  / r,
  /bin/ r,
  /bin/dash rix,
  /bin/grep rix,
  /bin/mkdir rix,
  /bin/mv rix,
  /bin/ps rUx,
  /bin/readlink rix,
  /bin/sed rix,
  /bin/touch rix,
  /bin/uname rUx,
  /bin/which rix,
  /boot/initrd.img-2.6.*generic r,
  /boot/vmlinuz-2.6.*generic r,
  /dev/oss/oss_hdaudio0/pcm0 w,
  /dev/shm/ rw,
  /dev/shm/** mrwk,
  /etc/chromium-browser/policies/*/ r,
  owner /home/*/ r,
  owner /home/*/** mwk,
  /home/*/** r,
  /proc/ r,
  /proc/*/cmdline r,
  owner /proc/*/environ r,
  /proc/*/fd/ r,
  owner /proc/*/io r,
  owner /proc/*/oom_adj w,
  /proc/*/smaps r,
  /proc/*/stat r,
  /proc/*/statm r,
  /proc/*/status r,
  owner /proc/*/task/ r,
  /proc/filesystems r,
  /proc/meminfo r,
  /proc/stat r,
  /proc/sys/kernel/* r,
  /proc/tty/drivers r,
  /proc/uptime r,
  /proc/version r,  
  /usr/bin/ark rUx,
  /usr/bin/basename rix,
  /usr/bin/cut rix,
  /usr/bin/eog rUx,
  /usr/bin/evince rPx,
  /usr/bin/file-roller rUx,
  /usr/bin/gawk rix,
  /usr/bin/gconftool-2 rix,
  /usr/bin/gedit rUx,
  /usr/bin/gimp* rUx,
  /usr/bin/gnome-network-properties rix,
  /usr/bin/gnome-open rix,
  /usr/bin/okular rUx,
  /usr/bin/oocalc rUx,
  /usr/bin/oodraw rUx,
  /usr/bin/ooffice rUx,
  /usr/bin/ooimpress rUx,
  /usr/bin/oowriter rUx,
  /usr/bin/setarch rix,
  /usr/bin/xarchiver rUx,
  /usr/bin/xdg-mime rix,
  /usr/bin/xdg-open rix,
  /usr/lib/chromium-browser/** rwkix,
  /usr/lib/gstreamer0.10/gstreamer-0.10/gst-plugin-scanner rix,
  /usr/lib/nspluginwrapper/i386/linux/npviewer rUx,
  /usr/lib/nspluginwrapper/i386/linux/npviewer.bin rix,
  /usr/lib/openoffice/program/soffice rUx,
  /usr/lib{,32,64}/** mr,
  /usr/local/lib/lib*so* mr,
  /var/lib/flashplugin-installer/npwrapper.libflashplayer.so mr,
  
}
```

---

### Post by bone2006 on 2010-09-14
Thanks everyone
Really appreciate the help and information

---

### Post by bone2006 on 2010-09-17
Just wanted to reply really quick about the original printing to pdf at ~/.ssh
the original profile did prevent it, I guess I had to restart the browser when I applied the profile. Because when I rebooted I noticed printing to pdf didn't work on many directories.

When i need some functionality that the profile is preventing, I just type in sudo /etc/init.d/apparmor stop, then accomplish the task and then turn it back on sudo /etc/init.d/apparmor start

I'm really impressed with apparmor and appreciate all the help with it.

---

### Post by bodhi.zazen on 2010-09-18
> **bone2006 said:**
> Just wanted to reply really quick about the original printing to pdf at ~/.ssh
the original profile did prevent it, I guess I had to restart the browser when I applied the profile. Because when I rebooted I noticed printing to pdf didn't work on many directories.

When i need some functionality that the profile is preventing, I just type in sudo /etc/init.d/apparmor stop, then accomplish the task and then turn it back on sudo /etc/init.d/apparmor start

I'm really impressed with apparmor and appreciate all the help with it.

You do not need to stop all of apparmor, put the profile in question into complain mode

```
sudo aa-complain chromium
```

do you task

re-enable

```
sudo aa-enforce chromium
```

Better, tweak the aa profile.

---

