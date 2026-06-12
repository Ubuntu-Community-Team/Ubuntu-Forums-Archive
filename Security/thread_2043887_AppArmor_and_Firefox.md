---
title: "AppArmor and Firefox"
date: 2012-08-17
forum: Security
---

### Post by thnewguy on 2012-08-17
I recently enabled the Firefox profile in AppArmor. I'm fairly new to AppArmor, but looking through the default profile it looks as though Firefox should be able to read from just about anywhere, but only be able to write to a few key folders. Folders that contain extensions, bookmarks, the ~/Downloads folder, etc.

To test this, after I enabled the Firefox AppArmor profile (aa-enforce /etc/apparmor.d/usr.bin.firefox), I went to a random site and attempted to download some files. I was able to save them to any location under my home folder.

Is this normal behaviour? It was my intension to sandbox Firefox so it could only write to its configuration folders and my Downloads folder, but the process seems to have all the access my regular user does. Am I missing a step? How do I lock down the browser so it can only write to folders I grant in the AppArmor profile?

---

### Post by Hungry Man on 2012-08-17
Well first of all it should be aa-enforce /etc/apparmor.d/usr.bin.firefox not /usr/apparmor.d/blahblahblah

Your Firefox profile probably lets you write to the entire user directory as that would provide compatibility (allows you do download) but it isn't that dangerous.

I don't have the default profile memorized though.

You can check that the process is contained by using 'aa-status' - this should list all of your enforced processes.

---

### Post by thnewguy on 2012-08-17
The /usr in place of /etc was a typo.
According to the apparmour status check the Firefox profile is enabled and set to enforcing. According to the profile it looks as though only the configuration and Downloads folder can be written to. Everything else looks to be marked read-only. Still, I can open and write to any file under my profile. This doesn't seem like correct behaviour. 

This is the relevant part of the profile.
```

  # Default profile allows downloads to ~/Downloads and uploads from ~/Public
  owner @{HOME}/ r,
  owner @{HOME}/Public/ r,
  owner @{HOME}/Public/* r,
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,

```

It looks to me like it's allowing Firefox to read my home folder (in order to grant access to sub-folders) and it allows the reading of files from Public. It then also enabled read and write for the Downloads folder. But if I create a new folder, call it "~/temp", I can save files to that folder from within Firefox.

> 
Your Firefox profile probably lets you write to the entire user directory as that would provide compatibility


It would also entirely remove the point of having an AppArmor profile for Firefox. Why enable a security profile if it continues to allow the process to behave exactly the same way it did before?

---

### Post by Hungry Man on 2012-08-17
> It would also entirely remove the point of having an AppArmor profile for Firefox. Why enable a security profile if it continues to allow the process to behave exactly the same way it did before?

Because you can block some globally readable areas that can be very useful for attackers who have already gotten onto your system and are now within the sandbox.

You can also restrict them even if they get a root exploit/ elevation exploit. Without Apparmor they would have nearly full access to the entire system.

The idea is entirely to let the process act exactly as it did before but to not be able to do anything more.

If your Firefox isn't being restricted at all can you check aa-status to make sure it's confined?

---

### Post by thnewguy on 2012-08-18
Yes, I checked aa-status and it shows the Firefox process is being confined under an enforcing policy. However, I am still able to read every part of the file system, including places like /boot, /var, /usr... And I can write to any location my user has write access to. This is a regular user account so it's not as though Firefox has root access.

---

### Post by bodhi.zazen on 2012-08-19
Sounds as if something is not working. Did you re-start firefox ?

Firefox will need to access large parts of the file system. If you wish to further restrict access, beyond the default profile, you will have to learn to write aa profiles ;)

---

### Post by rookcifer on 2012-08-19
The OP is correct and I had noticed this myself a while back.  So I examined the firefox profile and tracked down the issue.  

The issue is with the abstractions in the profile.  Even though it is supposed to allow downloads only to the "Downloads" directory, there are abstractions that bypass this and allow it to download to anywhere.  The problem file is in 

```
/etc/abstractions/ubuntu-browsers.d/user-files
```

Open that file and notice how it has the following line:
```

owner @{HOME}/** w,
```

What you need to do is comment out that line (use the hash tag symbol).  When you do this Firefox will follow the download rules outlined in the usr.bin.firefox profile itself.  I have tested it on 12.04 and it works.

This should probably be reported as a bug in fact.  The profile maintainer simply overlooked this abstraction and didn't realize they conflicted.

---

### Post by thnewguy on 2012-08-19
Thank you, rookcifer. I changed the line in the abstractions file and that helped me focus on the Firefox profile itself. There are still some problems.

For example, the Firefox profile by itself still allows me to write a file anywhere in my home folder, not just in my Downloads folder. A little playing around with the profile and I discovered a few things.

1. I could block access to my home folder and sub directories using
"deny @{HOME}/ w,
However, doing this means I can't save anywhere, including the Downloads folder, even though
owner @{HOWE]/Downloads/* rw,
is specified later in the file. It looks like the deny option overrides the allow option, regardless of the order of the rules.

2. I can restrict access to specific folders of my home (and other parts of the file system), but I have to specify them individually. So I can use
deny @{HOME}/Music w,
deny @{HOME]/Documents rwx,
deny @{HOME}/Photos w,
...
...
Though it's a royal pain to write them all out and the profile is global so it also blocks other users from writing to their folders. The only way to get around this seems to be specifying my entire path in the profile, ie
deny /home/newguy/Photos w,
deny /home/newguy/Music w,
...
...

Not ideal, but it will work. With a little more trial and error I think I can get the browser (and other apps) locked down. Thank you all for your help.

---

### Post by gray123 on 2012-08-24
> **thnewguy said:**
> Thank you, rookcifer. I changed the line in the abstractions file and that helped me focus on the Firefox profile itself. There are still some problems.

For example, the Firefox profile by itself still allows me to write a file anywhere in my home folder, not just in my Downloads folder. A little playing around with the profile and I discovered a few things.

1. I could block access to my home folder and sub directories using
&quot;deny @{HOME}/ w,
However, doing this means I can't save anywhere, including the Downloads folder, even though
owner @{HOWE]/Downloads/* rw,
is specified later in the file. It looks like the deny option overrides the allow option, regardless of the order of the rules.

2. I can restrict access to specific folders of my home (and other parts of the file system), but I have to specify them individually. So I can use
deny @{HOME}/Music w,
deny @{HOME]/Documents rwx,
deny @{HOME}/Photos w,
...
...
Though it's a royal pain to write them all out and the profile is global so it also blocks other users from writing to their folders. The only way to get around this seems to be specifying my entire path in the profile, ie
deny /home/newguy/Photos w,
deny /home/newguy/Music w,
...
...

Not ideal, but it will work. With a little more trial and error I think I can get the browser (and other apps) locked down. Thank you all for your help.

 Hi,      as a total newbie myself I found this thread the most useful I have found. I also want to tie down firefox and all other net based applications. About the deny /home/ w. I thought that it honours the first rule so if you allow ~/downloads/* rw and then deny /home/* w rather than the other way around it might work. I too wish to allow only write access to the download directory - its what I do anyway Cheers G

---

### Post by thnewguy on 2012-08-24
I think that works. I put a line at the bottom of my Firefox profile which reads

deny @{HOME}/ w,

And as long as I list the specific folders I want to have write access to _above_ that line it seems to work. So I guess with AppArmor the specific pieces need to go at the top and general statements go toward the bottom of the profile.

---

### Post by kleenex on 2012-08-24
Hi **thnewguy**. First off, thank You for the attempt to improve Firefox profile. I have a request to You. Could you write/paste here or write to me a personal message with Your current, improved Firefox profile? I mean the amendments relating to access to the user directory by Firefox etc. I would be grateful!

Oh, and one more thing. I'm thinking of creating a profile for Pidgin. As an example I would like to use profile for 12.04 Release: [usr.bin.pidgin]("https://bazaar.launchpad.net/%7Eapparmor-dev/apparmor-profiles/master/view/head:/ubuntu/12.04/usr.bin.pidgin"), with last revision on 2011-10-1. There is also version for 12.10 Release created on 2012-05-01. My question: Both profiles contain, for example, something like this: **/usr/bin/gnome-network-preferences ix** (line # 57). But I see that in Xubuntu 12.04 there is no such file in [COLOR=SeaGreen]/usr/bin/[/COLOR] directory. What should I do? Remove this line or just comment out? Really, I do not know. 

Thanks.

---

### Post by thnewguy on 2012-08-24
I'm really just learning how to trouble shooting AppArmor, so I'm afraid I'm not in a position to help much, though perhaps someone else here can. As for my Firefox profile, this is what I have thus far in /etc/apparmor.d/usr.bin.firefox

```

# vim:syntax=apparmor
# Author: Jamie Strandboge <jamie@canonical.com>

# Declare an apparmor variable to help with overrides
@{MOZ_LIBDIR}=/usr/lib/firefox

#include <tunables/global>

# We want to confine the binaries that match:
#  /usr/lib/firefox/firefox
#  /usr/lib/firefox/firefox
# but not:
#  /usr/lib/firefox/firefox.sh
/usr/lib/firefox/firefox{,*[^s][^h]} {
  #include <abstractions/audio>
  #include <abstractions/cups-client>
  #include <abstractions/dbus-session>
  #include <abstractions/gnome>
  #include <abstractions/nameservice>
  #include <abstractions/p11-kit>

  # Addons
  #include <abstractions/ubuntu-browsers.d/firefox>

  # for networking
  network inet stream,
  network inet6 stream,
  @{PROC}/[0-9]*/net/if_inet6 r,
  @{PROC}/[0-9]*/net/ipv6_route r,
  @{PROC}/[0-9]*/net/dev r,
  @{PROC}/[0-9]*/net/wireless r,

  # should maybe be in abstractions
  /etc/ r,
  /etc/mime.types r,
  /etc/mailcap r,
  /etc/xdg/*buntu/applications/defaults.list    r, # for all derivatives
  /usr/share/xubuntu/applications/defaults.list r,
  owner @{HOME}/.local/share/applications/defaults.list r,
  owner @{HOME}/.local/share/applications/mimeapps.list r,
  owner @{HOME}/.local/share/applications/mimeinfo.cache r,
  owner /tmp/** m,
  owner /var/tmp/** m,
  /tmp/.X[0-9]*-lock r,

  /etc/timezone r,
  /etc/wildmidi/wildmidi.cfg r,

  # firefox specific
  /etc/firefox*/ r,
  /etc/firefox*/** r,
  /etc/xul-ext/** r,
  /etc/xulrunner-2.0*/ r,
  /etc/xulrunner-2.0*/** r,
  /etc/gre.d/ r,
  /etc/gre.d/* r,

  # noisy
  deny @{MOZ_LIBDIR}/** w,
  deny /usr/lib/firefox-addons/** w,
  deny /usr/lib/xulrunner-addons/** w,
  deny /usr/lib/xulrunner-*/components/*.tmp w,
  deny /.suspended r,
  deny /boot/initrd.img* r,
  deny /boot/vmlinuz* r,
  deny /var/cache/fontconfig/ w,
  deny @{HOME}/.local/share/recently-used.xbel r,

  # TODO: investigate
  deny /usr/bin/gconftool-2 x,

  # These are needed when a new user starts firefox and firefox.sh is used
  @{MOZ_LIBDIR}/** ixr,
  /usr/bin/basename ixr,
  /usr/bin/dirname ixr,
  /usr/bin/pwd ixr,
  /sbin/killall5 ixr,
  /bin/which ixr,
  /usr/bin/tr ixr,
  @{PROC}/ r,
  @{PROC}/[0-9]*/cmdline r,
  @{PROC}/[0-9]*/mountinfo r,
  @{PROC}/[0-9]*/stat r,
  owner @{PROC}/[0-9]*/task/[0-9]*/stat r,
  @{PROC}/[0-9]*/status r,
  @{PROC}/filesystems r,
  owner @{HOME}/.thumbnails/*/*.png r,

  /etc/mtab r,
  /etc/fstab r,

  # Needed for the crash reporter
  owner @{PROC}/[0-9]*/environ r,
  owner @{PROC}/[0-9]*/auxv r,
  /etc/lsb-release r,
  /usr/bin/expr ix,
  /sys/devices/system/cpu/ r,
  /sys/devices/system/cpu/** r,

  # about:memory
  owner @{PROC}/[0-9]*/statm r,
  owner @{PROC}/[0-9]*/smaps r,

  # Needed for container to work in xul builds
  /usr/lib/xulrunner-*/plugin-container ixr,

  # allow access to documentation and other files the user may want to look
  # at in /usr and /opt
  /usr/ r,
  /usr/** r,
  /opt/ r,
  /opt/** r,

  # so browsing directories works
  / r,
  /**/ r,

  # Default profile allows downloads to ~/Downloads and uploads from ~/Public
  owner @{HOME}/ r,
  owner @{HOME}/Public/ r,
  owner @{HOME}/Public/* r,
  owner @{HOME}/Downloads/ r,
  owner @{HOME}/Downloads/* rw,

  # per-user firefox configuration
  owner @{HOME}/.{firefox,mozilla}/ rw,
  owner @{HOME}/.{firefox,mozilla}/** rw,
  owner @{HOME}/.{firefox,mozilla}/**/*.{db,parentlock,sqlite}* k,
  owner @{HOME}/.{firefox,mozilla}/plugins/** rm,
  owner @{HOME}/.{firefox,mozilla}/**/plugins/** rm,
  owner @{HOME}/.config/ibus/bus/ w,
  owner @{HOME}/.gnome2/firefox*-bin-* rw,

  #
  # Extensions
  # /usr/share/.../extensions/... is already covered by '/usr/** r', above.
  # Allow 'x' for downloaded extensions, but inherit policy for safety
  owner @{HOME}/.mozilla/**/extensions/** mixr,

  deny @{MOZ_LIBDIR}/update.test w,
  deny /usr/lib/mozilla/extensions/**/ w,
  deny /usr/lib/xulrunner-addons/extensions/**/ w,
  deny /usr/share/mozilla/extensions/**/ w,
  deny /usr/share/mozilla/ w,

  deny @{HOME}/ w,

  # Miscellaneous (to be abstracted)
  # Ideally these would use a child profile. They are all ELF executables
  # so running with 'Ux', while not ideal, is ok because we will at least
  # benefit from glibc's secure execute.
  /usr/bin/mkfifo Uxr,  # investigate
  /bin/ps Uxr,
  /bin/uname Uxr,

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.bin.firefox>
}

```


The above profile allows Firefox to read from my home folder (still trying to lock that down), but prevents writing to most places except for Firefox's configuration folders and the Downloads folder. I tried to lock it down further, but apparently there is a PID file somewhere and if Firefox can't create this file then it refuses to run. So this isn't a perfect solution, but it is a little more secure than running without AppArmor.

---

### Post by kleenex on 2012-08-25
Hi, thank You **thnewgu**. Now it will be much easier for my to improve Firefox profile. And what about Pidgin and **/usr/bin/gnome-network-preferences ix**? Do You know something about this?

---

### Post by thnewguy on 2012-08-25
I haven't done any work on profiles other than web browsers,sorry.

---

### Post by rookcifer on 2012-08-25
> **thnewguy said:**
> Thank you, rookcifer. I changed the line in the abstractions file and that helped me focus on the Firefox profile itself. There are still some problems.

For example, the Firefox profile by itself still allows me to write a file anywhere in my home folder, not just in my Downloads folder. A little playing around with the profile and I discovered a few things.

It shouldn't.  I have my profile setup as I described and it does not allow writing to anywhere but /Downloads.

---

