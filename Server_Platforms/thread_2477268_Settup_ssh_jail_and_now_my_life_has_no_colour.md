---
title: "Settup ssh jail and now my life has no colour"
date: 2022-07-19
forum: Server Platforms
---

### Post by bigmonmulgrew on 2022-07-19
I've been setting up a server (22.04) and I've been testing setting up a jail with jailkit. 

When I log in with a user outside the jail I get colours on my command line with all sorts of things, ls and nano for example.

When I log in with a user inside the jail everythign is white.

Google has led me to visit .bashrc and set force_color_prompy to true but this makes no difference.

Obviously I know I'm missing something required for colour in my jail but I don't know what. How do I get colours back inside the jail?

---

### Post by TheFu on 2022-07-19
Do you realize that chroot support is built-into ssh, right?

As for color use, I don't know, since I specifically disable all color use in all my terminals. I find green on black soothing.

---

### Post by TheFu on 2022-07-19
The sshd_config manpage:
```
     ChrootDirectory
             Specifies the pathname of a directory to chroot(2) to after authentication.  At ses&#8208;
             sion startup sshd(8) checks that all components of the pathname are root-owned direc&#8208;
             tories which are not writable by any other user or group.  After the chroot, sshd(8)
             changes the working directory to the user's home directory.  Arguments to
             ChrootDirectory accept the tokens described in the TOKENS section.

             The ChrootDirectory must contain the necessary files and directories to support the
             user's session.  For an interactive session this requires at least a shell, typically
             sh(1), and basic /dev nodes such as null(4), zero(4), stdin(4), stdout(4), stderr(4),
             and tty(4) devices.  For file transfer sessions using SFTP no additional configuration
             of the environment is necessary if the in-process sftp-server is used, though sessions
             which use logging may require /dev/log inside the chroot directory on some operating
             systems (see sftp-server(8) for details).

             For safety, it is very important that the directory hierarchy be prevented from modi&#8208;
             fication by other processes on the system (especially those outside the jail).  Mis&#8208;
             configuration can lead to unsafe environments which sshd(8) cannot detect.

             The default is none, indicating not to chroot(2).

```

---

### Post by bigmonmulgrew on 2022-08-01
Yes I've used that in the past, this time I figured I would experiment with jailkit.

This is the part I have found immensely useful

"The ChrootDirectory must contain the necessary files and directories to support the user's session."

I have found jailkit very useful in managing which files are included in the jail.

Are you suggesting there are issues with using jailkit?

---

### Post by TheFu on 2022-08-01
> **bigmonmulgrew said:**
>  Are you suggesting there are issues with using jailkit?

Not at all, just that there is a built-in method that works and is well-used, well-tested. Since it is included with the ssh software distribution, it is what I use. Nothing more.  There are 50-500 ways to accomplish things on Unix systems.  Unless you try them, which is easiest and meets your specific needs won't be known.  In these forums, we often see people trying to do something the hard way because they don't know better.  

Choosing to use a specific tool is a different thing entirely.
I suppose you've seen this: [https://www.howtoforge.com/debian-9-jail-jailkit/](https://www.howtoforge.com/debian-9-jail-jailkit/) - while I'm not a fan of using source code on my systems anymore, if you need the latest features/fixes, that could be a valid argument.  I did my time with source packages in the 1990s and never want to return to those days of manually following dependencies and building each of those just to discover that the dependency has 5 dependencies too.  

As you probably know, jails (really chroot environments) are just roadblocks, not full security, but then what is?  

If it were me allowing unknown people into a system, a linux container would be my choice. It uses namespaces, cgroups AND chroot to simulate a different system.  With lxd, it is trivial to setup a little ssh system to allow access to untrusted people, though not nearly as storage efficient.  An lxd container can be tiny if we use a tiny distro like alphine as the base (less than 20MB).  With Ubuntu Server as the base, I think about 600MB is needed.  I can spin up a 22.04 container in a few seconds, connect, add a user, setup ssh for that that user and be done in about 2 minutes.  The container will run unprivileged.  With Alpine, it will take me a bit longer because I'm not as familiar with the package system, but it would be less than 5 minutes of effort.  Of course, I'd put the container on a LAN separate from all my other systems and forward one of my public IPs to that specific system.

Hummmm.  Think I need to add this to my list of things to play with this week.  Thanks for the idea.  I've setup an alpine container before, but haven't done the added network stuff.  I have a few free IPs remaining still.  Alas, other priorities need to happen today.

---

### Post by bigmonmulgrew on 2022-08-01
lol gald I can help, and thanks for the advice.

The thing that drew me to jailkit was its ability to manage packages in the jail.

While I can manually move all the necessary files into the jail I imagine I would have to write something to manage them as jailkit does. If you have any recommendations for alternatives I'm happy to test them out, I just inherited 6 raspberry pis so now I have plenty of boxes to toy around with projects with.

"not full security, but then what is? "   If we could actually get to a point where most systems are 100% secure I imagine many of us would be out of a job.

---

### Post by TheFu on 2022-08-01
> **bigmonmulgrew said:**
>  
"not full security, but then what is? "   If we could actually get to a point where most systems are 100% secure I imagine many of us would be out of a job.

Any system that is powered on isn't secure and it will always be that way.  Add a GUI, it is less secure. Add networking, and it is even less secure.  Let uninformed humans use the system and there's no chance for it to be secure.  Let informed humans use it, and security raises a tiny bit, but with 1 click or 1 command, all the security in the world can be removed - since we are all human (well, most of us anyways), we will make mistakes and raise the risks unintentionally. If our timing is bad, game over.

---

### Post by kevdog on 2022-08-02
The Alpine Linux LXD container sounds like a fun project.  I've used alpine as base images for docker containers but never in lxd.

---

