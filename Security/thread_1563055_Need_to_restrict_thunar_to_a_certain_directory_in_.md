---
title: "Need to restrict thunar to a certain directory in ubuntu"
date: 2010-08-28
forum: Security
---

### Post by joelwhrs on 2010-08-28
I have created my own custom ubuntu distro using the alternate installation cd and doing a command line install. I'm using ubuntu 10.04 as my base and am also using thunar as my file browser and am trying to create a secure desktop environment and to do that I'd like to restrict thunar to a certain partition. Is it possible to do that?

---

### Post by joelwhrs on 2010-08-30
Anyone? If it is not possible with Thunar is there any other file browser with that functionality?

---

### Post by bodhi.zazen on 2010-08-30
> **joelwhrs said:**
> I have created my own custom ubuntu distro using the alternate installation cd and doing a command line install. I'm using ubuntu 10.04 as my base and am also using thunar as my file browser and am trying to create a secure desktop environment and to do that I'd like to restrict thunar to a certain partition. Is it possible to do that?

No it is not possible to do that.

Learn to use apparmor.

---

### Post by joelwhrs on 2010-09-02
How would I go about using apparmor to restrict the file system. All that I have seen that it does it protect apps. I don't quite understand how to even do that. Is there a good tutorial for it somewhere?

---

### Post by bodhi.zazen on 2010-09-03
The answer , or my suggestion, is in two parts.

First you can not easily restrict a user to a single directory, such as his or her home directory, easily. They need access to many system files and applications, /bin/bash , ssh, scp, ftp, etc, etc, depending on what you are wanting them to do exactly.

The easiest way to do something like this would be a chroot

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

You can chroot single applications, such as ssh or apache.

[http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian)

You probably do not want a chroot, but perhaps you may. The point is you need to allow access to various system files in some way, either in a chroot or allowing access to system files.

Normally this is done with linux permissions. Say you want to deny access to /media/some_directory, you would set the ownership and permissions on the directory to restrict access.

For example, on your home directory, 

```
chmod 700 ~
```

If you need more then linux permissions, then at least on Ubuntu you will need either a chroot or apparmor.

Part 2 - Apparmor

What you would do is make a link to /bin/bash , I call it "jailbash"

```
sudo ln /bin/bash /usr/local/jailbash
```

You then change the users log in shell from bash to jailbash

```
sudo chsh <user>
```

Now write an apparmor profile for jailbash:

Here is an example :

[http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.local.bin.jailbash](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.local.bin.jailbash)

That profile may be more or less restrictive then you want, you will need to adapt it to your needs.

It depends, is this ssh ? ftp ? shell access ? are you going to allow running X ? etc, etc, etc. You have not provided much in the way of details of what you are doing exactly, so hard to give you more specific advice. Perhaps all you need is standard permissions + encryption, or perhaps you need to install ssh + keys + forced commands, or a chroot, or vsftp, hard to know.

---

### Post by joelwhrs on 2010-09-03
I'm running X, and using openbox as my window manager. The only programs that I want the end user to have access to is a file browser to view Documents folder, the openoffice suite, gnucash, and a simple scheduler. What I want to do is create a restricted operating system that allows anyone who uses it to use those programs and then let them save it in the documents folder. I also want them to be able to view external drives which I currently got working using thunar. I want absolutely no internet but possibly file sharing under the final user profile. I also have an administration account and I want that to have full administration rights. Is all this possible?

---

### Post by bodhi.zazen on 2010-09-03
> **joelwhrs said:**
> I'm running X, and using openbox as my window manager. The only programs that I want the end user to have access to is a file browser to view Documents folder, the openoffice suite, gnucash, and a simple scheduler. What I want to do is create a restricted operating system that allows anyone who uses it to use those programs and then let them save it in the documents folder. I also want them to be able to view external drives which I currently got working using thunar. I want absolutely no internet but possibly file sharing under the final user profile. I also have an administration account and I want that to have full administration rights. Is all this possible?

It is possible, but will take some work. With what you describe I would suggest a combination of apparmor and iptables.

---

### Post by joelwhrs on 2010-09-24
I have been checking around and I think what I am looking for is something like chroot. I want my home folder to be the top directory but I will be running quite a few programs on it. According to the post above I am able to chroot only a single program but I was doing research on it and have not found a method of doing that.

Something that would be really great is if I could make the home directory root but still access certain folder in the real root, but if I understand correctly this is not possible. The programs that I would need to be able to run are; Openoffice, thunar w/ automount, gnucash, quasar, epdfview, image viewing program of some sorts, idesk, and tint2. I think that covers the important ones that I will be running. Any help would be greatly appreciated.

---

### Post by bodhi.zazen on 2010-09-24
> **joelwhrs said:**
> I have been checking around and I think what I am looking for is something like chroot. I want my home folder to be the top directory but I will be running quite a few programs on it. According to the post above I am able to chroot only a single program but I was doing research on it and have not found a method of doing that.

Something that would be really great is if I could make the home directory root but still access certain folder in the real root, but if I understand correctly this is not possible. The programs that I would need to be able to run are; Openoffice, thunar w/ automount, gnucash, quasar, epdfview, image viewing program of some sorts, idesk, and tint2. I think that covers the important ones that I will be running. Any help would be greatly appreciated.

As I indicated earlier, apparmor (jailbash) is going to be far, far, far easier.

If you are going to do a chroot, you need to make all the directories in your /home and copy all the system files, binaries, and libs. This will be an extensive list. You would then need to manually update them (apt-get will not keep the files up to date) and interface with X. A chroot would be a ton of work. Normally I run X apps in a chroot by ssh into the chroot and forwarding the apps, so logging into a chroot via GDM, good luck with that.

See my previous post on jailbash.

---

### Post by joelwhrs on 2010-09-24
Ok, I was reading your post about jailbash and did not quite understand it. I did a few google searches and nothing really came up either. How would I customize it to my liking and exactly what does it all do?

---

