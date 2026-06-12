---
title: "[SOLVED] rkhunter warnings, virus?"
date: 2008-09-07
forum: Security
---

### Post by Camilia on 2008-09-07
Ran rkhunter and
/usr/sbin/unhide                                         [ Warning ]
/usr/sbin/unhide-linux26                                 [ Warning ]
 Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

Does anyone know what this means and what I should do about it? Hopefully not viruses.

---

### Post by mb_webguy on 2008-09-07
> **Camilia said:**
> Ran rkhunter and
/usr/sbin/unhide                                         [ Warning ]
/usr/sbin/unhide-linux26                                 [ Warning ]
 Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

Does anyone know what this means and what I should do about it? Hopefully not viruses.

Well, first off, even if those directories do contain viruses, you don't need to concern yourself terribly much, since a virus can't do anything on Linux.  You could pass it on to a Windows user if you transfer the file to them, but you'd have to do it yourself, since -- as I said -- the virus can't do it on its own in Linux.

Second... Wow.  Those are some extraordinarily unhelpful warning messages.  I don't know much (or actually anything) about rkhunter, but you may want to try installing the [Linux version of AVG]("http://free.avg.com/ww.download?prd=afl") and see what it says.

---

### Post by 3rdalbum on 2008-09-07
Rkhunter doesn't look for viruses, it looks for rootkits. Linux rootkits, not Windows ones.

The /dev and "hidden files and directories" warnings are something I've always had; I suggest ignoring those. The warnings about the unhide program are probably also false alarms - they are used by rkhunter. If you're worried about them, you can use Synaptic Package Manager to reinstall "unhide".

Rkhunter also has a log file that gives more information; at the end of your scan it should tell you the location of it.

If you're running an up-to-date system, and you don't have any outward-facing services accessible from the Internet (i.e. your router has a firewall that doesn't have any ports allowed), then there is no realistic way you can get a rootkit.

---

### Post by Camilia on 2008-09-07
Read this could be due to updates thus pasted sudo rkhunter—propupd in terminal. Then pasted /sudo rkhunter -c -sk in terminal and get /sudo: No such file or directory

Sometimes can run check and sometimes can't. This concerns me. Why could this be?

I have the unhide program installed.

---

### Post by mb_webguy on 2008-09-07
> **3rdalbum said:**
> Rkhunter doesn't look for viruses, it looks for rootkits. Linux rootkits, not Windows ones.

The /dev and "hidden files and directories" warnings are something I've always had; I suggest ignoring those. The warnings about the unhide program are probably also false alarms - they are used by rkhunter. If you're worried about them, you can use Synaptic Package Manager to reinstall "unhide".

Rkhunter also has a log file that gives more information; at the end of your scan it should tell you the location of it.

If you're running an up-to-date system, and you don't have any outward-facing services accessible from the Internet (i.e. your router has a firewall that doesn't have any ports allowed), then there is no realistic way you can get a rootkit.

See... I said I didn't know anything about rkhunter, didn't I?  The OP said viruses, so...  *shrug*

;)

---

### Post by Camilia on 2008-09-09
There is no realistic way you can get a rootkit I am told

Since I got trojan viruses on windows xp just after I copied pictures for my avatar I have gotten a little paranoid. Thus I like scan my computer at times.

---

### Post by Oldsoldier2003 on 2008-09-09
Moved from general help

---

### Post by jerome1232 on 2008-09-09
> **Camilia said:**
> There is no realistic way you can get a rootkit I am told

Since I got trojan viruses on windows xp just after I copied pictures for my avatar I have gotten a little paranoid. Thus I like scan my computer at times.

Generally you'd have to either install the root kit, or an attacker gain access to your system and install the root kit. Root kits get installed into a system that has already been compromised to guarantee the attacker has a back door in and to cover their tracks.

This is more of a concern for servers, do you have any servers installed, like openssh? Is it avaible to the internet? If not I wouldn't worry about rootkits, really.

Viruses not so much either.

Phishing sites, yes, browsers security yes, for firefox addons like noscript and adblock help alot.

---

### Post by Camilia on 2008-09-09
No I don't have a server.  My computer is simply connected via cable to the internet.

Now I am certain I don't need to worry about roots.

---

