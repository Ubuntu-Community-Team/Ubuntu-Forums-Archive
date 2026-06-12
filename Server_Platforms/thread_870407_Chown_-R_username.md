---
title: "Chown -R username /"
date: 2008-07-25
forum: Server Platforms
---

### Post by mrfr0g on 2008-07-25
While working on the server today, I did something really stupid. 

sudo chown -R username /

I realized my mistake just after I pressed enter. Now I'm trying to fix my permissions without reinstalling.

The first problem I ran in to,

 sudo: /etc/sudoers is owned by uid 1000, should be 0, can't sudo 

I was able to reset it to root:root, and chmod it to 0440. Unfortunately now when ever I try to 'sudo' something it asks for my password, when I type it in, nothing happens, it just goes back to the prompt. When I type in an incorrect password it tells me it was incorrect, so it seems that it is reading the password file, but just isn't assigning me the super user permissions.

Has anyone else come across this? Anyone know how to fix this without reinstalling everything?

---

### Post by Rocket2DMn on 2008-07-25
I think for the most part you are out of luck.  Unless the damage was very minimal, you may be able to fix permissions by using the recovery mode kernel at the GRUB screen which gives you a root terminal.  Even if you manage to "fix" stuff, it is very possible that things are still not how they should be, and you may have opened up security holes along with a whole pandora's box of problems.

If you reinstall, don't forget to backup your data beforehand.

---

### Post by mrfr0g on 2008-07-26
Well it was worth a shot. Thank you.

---

### Post by pdwerryhouse on 2008-07-27
Actually, one way to fix things might be to boot into single user mode, mount all the filesystems and bring up the network manually, and then run this:

```
apt-get --reinstall install $(dpkg --get-selections | awk '{print $1}')
```

That will reinstall every package on your system. You might like to start with just some of the required packages to get it going quickly:

```
apt-get --reinstall install base-files base-passwd bash bsdutils coreutils dash debianutils diff dpkg e2fslibs e2fsprogs findutils gcc-4.2-base grep gzip hostname initscripts libacl1 libattr1 libblkid1 libc6 libcap1 libcomerr2 libdevmapper1.02 libdevmapper1.02.1 libgcc1 libncurses5 libpam-modules libpam-runtime libpam0g libselinux1 libsepol1 libslang2 libss2 libstdc++6 libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl libuuid1 login lsb-base lzma makedev mawk mktemp mount ncurses-base ncurses-bin passwd perl-base procps python-minimal python2.5-minimal sed startup-tasks system-services sysv-rc sysvutils tar tzdata upstart upstart-compat-sysv upstart-logd util-linux zlib1g
```

---

### Post by jdixon567 on 2010-08-17
This is for all you noobs like me that were about to give up hope and reinstall after a chown -R spree gone wrong.  I spent a year tweaking my ubuntu to be "mine" and I wasn't feeling the resinstall strategy.

This clever guy figured a way of fixing the permissions issue, the only difference is he chmoded (not chowned) his entire root directory.  He created a virtual machine of his ubuntu version, installed all the packages he has on his messed up machine, and copied the proper permissions back to his messed up machine using some bash script magic:

[http://wiki.joescove.com/Restoring_Ubuntu_default_file_permissions](http://wiki.joescove.com/Restoring_Ubuntu_default_file_permissions)

He didn't give a guide on creating the virtual machine, so I used VirtualBox to create a copy of Ubuntu 10.0.4.

Install:  [https://help.ubuntu.com/community/VirtualBox/Installation](https://help.ubuntu.com/community/VirtualBox/Installation)

Setup virtual machine for your ubuntu version:  

[https://help.ubuntu.com/community/VirtualBox/FirstVM](https://help.ubuntu.com/community/VirtualBox/FirstVM)

Since he used chmod and not chown, you need to modify his script to replace this line of his log_file_permissions.sh:

sudo find "/$folder" -exec stat --format="chmod %a %n" "{}" \; > "$folder.permissions"

with:

sudo find "/$folder" -exec stat --format="chown %U:%G %n" "{}" \; > "$folder.permissions"

Also, getting files from your virtual machine ubuntu to your broken ubuntu version is a requirement.  I used the shared folder's in virtualbox, but it was a little tricky for a noob like me to setup.

I hope this helps someone, you don't have to reinstall!

---

### Post by CharlesA on 2010-08-17
Did that really warrent bumping a 2 year old thread?

---

