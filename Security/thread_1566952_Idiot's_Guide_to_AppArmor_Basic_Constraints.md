---
title: "Idiot's Guide to AppArmor: Basic Constraints"
date: 2010-09-03
forum: Security
---

### Post by KonfuseKitty on 2010-09-03
OK, so I've read and re-read everything I can find about AppArmor, to no avail. On the whole, AppArmor isn't for me. However, rather than give up on it completely, I have an idea: create a profile that I could use as a template for any untrusted application, with the aim of 1) blocking it from network access and 2) blocking it from installing other applications. I've got as far as creating an empty profile:


```
# Generic AppArmor Profile for UntrustedApplication
# ------------------------------------------------------------------

#include <tunables/global>
/usr/sbin/UntrustedApplication {
#include <abstractions/base>

}

```


What do I need to add to make this profile 100% permissive, except for the two exceptions stated above?

---

### Post by Rubi1200 on 2010-09-03
> What do I need to add to make this profile 100% permissive, except for the two exceptions stated above?
Wouldn't it really depend on how "complicated" the program is and to what extent you want to restrict it?

For example, I know from reading posts by bodhi.zazen that an AppArmor profile for Firefox (and presumably other web browsers) is pretty complicated due to the nature of the application.

My suggestion is to start with something really easy, not web facing, and put the profile in complain mode so you can troubleshoot errors.

---

### Post by KonfuseKitty on 2010-09-03
Oh, well, if it is that complicated then never mind. I was kind of hoping that the answer to the networking question was to not enable it, and the installation blocking a matter of denying writing to certain directories. I guess it's not that easy - it was worth trying though. :)

---

### Post by uRock on 2010-09-03
Check out the AppArmor  profiles here to see how they are set up. They aren't very easy, but you may find the rules for the application your looking for. [http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/)

---

### Post by KonfuseKitty on 2010-09-03
Thanks, I'm aware of those profiles. The trouble is that I'm too ignorant of the Linux inner workings to make good use of them. It's not just a matter of downloading the profiles, you have to enter complain mode, then troubleshoot, edit the profiles, and maintain them in the future. That approach assumes you know what things mean when you read them in the logs, and when AppArmor presents options. I'm just not technical enough for that.


I also find it disconcerting that, for example, there's no shortage of advice how to enable networking, but I haven't read a confirmation yet that networking is disabled unless specifically enabled. Someone somewhere needs to consider the needs of us non-techies and create sets of rules we can apply generically. Here's more that I can think of:


* How to block execution of other programs
* How to block reading of passwords and keys
* How to block python, perl and ruby execution


And so on. The two questions I originally presented are what I thought was just the easiest, most essential stuff. If we can't get to a generic solution with that, then AppArmor is clearly not the solution for someone like me.

---

### Post by uRock on 2010-09-03
One day someone will create a GUI application for creating the profiles, but as long as Linux is as configurable as it is, these apps will not know where all of the files are stored to be able to protect them.

---

### Post by Rubi1200 on 2010-09-03
I know this is very technical, but OpenSUSE, which also implements AppArmor, has a "guide for geeks" that makes for interesting reading:
[http://en.opensuse.org/SDB:AppArmor_geeks](http://en.opensuse.org/SDB:AppArmor_geeks)

---

### Post by bodhi.zazen on 2010-09-03
If you are finding apparmor too complicated, come back to it once you feel more comfortable with Linux.

If you are interested, start with a simple application, such as Privoxy. You will need to watch the logs.

The basic syntax is not *that* complicated

apparmor blocked application foo from reading file bar

example 

apparmor blocked firefox from reading /etc/resolv.conf

you then add a line in the firefox profile

/etc/resolv.conf r,

If you use aa-logprof you can add some basic pre-built rules, such as for X or gnome, etc.

You can also use wild cards

/etc/** r,

I find it takes a few hours, but once the basic syntax clicks, it is much easier.

If you have a denial you do not understand, post the message and someone can help.

Unfortunately there is not default profile, or rather the default profile is to deny all access. You then allow only what is needed for the application to function normally.

---

### Post by KonfuseKitty on 2010-09-04
Thanks bodhi, I'll take your advice and leave it for a while. I've just spent quite some time trying to profile a program with the complain-logprof-enforce routine, until I gave up because when in enforce, the app wouldn't load. This method might work nicely on some straightforward applications like Privoxy, but it's frustrating otherwise, at least for me. I hope something faster and more effective is developed in time.


That said, I thought I had cracked it with my attempt to manually write a 100% permissive profile which I could then restrict as needed. As a permissive profile it worked, I set it for Opera and Opera worked without complaint. However, when I disabled networking in the profile, this had no effect, Opera continued to connect regardless. I'm curious as to why this is. My guess is that it's the ux option in the last line - is that correct?


```
# Generic 100% Permissive AppArmor Profile for UntrustedApplication

# profile usr.bin.opera in /etc/apparmor.d/

/usr/bin/opera {

  #For description of these POSIX capabilities see:
  #http://www.gentoo.org/proj/en/hardened/capabilities.xml

  capability chown,
  capability dac_override,
  capability dac_read_search,
  capability fowner,
  capability fsetid,
  capability kill,
  capability setgid,
  capability setuid,
  capability setpcap,
  capability linux_immutable,
  #capability net_bind_service,
  #capability net_broadcast,
  #capability net_admin,
  #capability net_raw,
  capability ipc_lock,
  capability ipc_owner,
  capability sys_module,
  capability sys_rawio,
  capability sys_chroot,
  capability sys_ptrace,
  capability sys_pacct,
  #capability sys_admin,
  #capability sys_boot,
  capability sys_nice,
  capability sys_resource,
  capability sys_time,
  capability sys_tty_config,
  capability mknod,
  capability lease,

  #network,
  
  /** rwklmux,

}
```

---

### Post by wacky_sung on 2010-09-05
I do agreed with KonfuseKitty after being trying with apparmor for more than 10 times with all the readup but still cannot get it to work properly.What i did is just to install grsecurity repository and all my problem solved.

---

### Post by uRock on 2010-09-05
I've installed a couple of the defaults and a couple of the definitions from bodhi.zazen's page.

---

