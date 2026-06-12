---
title: "Pam_Mount"
date: 2009-08-13
forum: Server Platforms
---

### Post by Ahlan on 2009-08-13
Hi,

I  am using Ubuntu 9.04 and don't seem to be able to get PAM_Mount to work.

I login using likewise to our AD domain and I can mount server shares using smbmount
however I would like to use Pam_Mount so that user shares are automatically mounted
at login and dismounted at logout.

If I login as Ahlan and issue the command from the home directory
smbmount //Jeremiah/Ahlan Work
it asks me for my password and then mounts  the share Ahlan from the server Jeremiah
at the mount point /home/ULTIMATE/ahlan/Work

To automate this I edited /etc/security/pam_mount.conf.xml
and uncommented the line
<luserconf name=".pam_mount.conf.xml"/>

I then added in my home directory (/home/ULTIMATE/ahlan) the file .pam_mount.conf.xml
containing

<pam_mount>
<volume
  user="*' fstype="smbfs" server="Jeremiah" path="Ahlan" mountpoint="~Work"
/>
</pam_mount>

I have checked common-auth and common-session.
These already have the lines
auth optional pam_mount.so try_first_pass
and
session optional pam_mount.so

although auth pam_mount.so doesn't seem to like either try_first_pass nor use_first_pass so I current use the line
auth optional pam_mount.so

However, try as I may nothing I do mounts the share.
Any clues as to what I am doing wrong or have misunderstood.

Please forgive any stupidity here because this is only my second day playing around with Linux, so everything is very new and I may have misunderstood vital stuff that is obvious to more experienced Linux/Ubunto users.

For example where are the error logs written?
What should I be looking for?

Any help much appreciated.

---

### Post by varanasi on 2009-12-14
Did you figure this out?  I have the same problem.

---

### Post by mvaldez on 2009-12-20
Hi. This is how I did it. I also use 9.04 at my workstation and Samba as server. In /etc/security/pam_mount.conf.xml I had to uncomment both

```
<luserconf name=".pam_mount.conf.xml" />
```

and 

```
<mntoptions allow="*" />
```

(the last one is in a block with two "mntoptions deny" options, but I only moved the "mntoptions allow" option out of the commented block.)


In /etc/pam.d I added/modified,

common-auth:
```
auth	optional	pam_mount.so try_first_pass
```

common-pammount:
```
auth       optional   pam_mount.so
session    optional   pam_mount.so
```

common-session:
```
session	optional	pam_mount.so try_first_pass
```


In the ~/.pam_mount.conf.xml I have:
```
<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<pam_mount>
<volume fstype="cifs" server="wintermute" path="mvaldez" mountpoint="/home/mvaldez/Mis_Documentos" options="iocharset=utf8,domain=biofmds,noperm" />
</pam_mount>
```
where "wintermute" is the name of the server, "mvaldez" is the name of my home dir/username in the server, "Mis_Documentos" is the mount point in my workstation, and "biofmds" is the Samba domain.

This works for me, however it always complains about "unknown pam_mount option try_first_pass". It mounts my remote home when I login in GDM or in the console (even remote with SSH).


Now, if I could only make this work in 9.10 Karmic Koala... ](*,)


Regards,

MV

---

### Post by mvaldez on 2009-12-24
Just to complete my last post... in Ubuntu 9.10 (Karmic Koala):

I modified only the /etc/security/pam_mount.conf.xml (didn't changed any file in /etc/pam.d/) and it is now like:

```
<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<pam_mount>
<debug enable="0" />
<luserconf name=".pam_mount.conf.xml" />
<mntoptions require="" />
<mntoptions allow="*" />
<!-- mntoptions deny="suid,dev" / -->
<!-- mntoptions require="nosuid,nodev" / -->
<path>/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin</path>
<logout wait="0" hup="0" term="0" kill="0" />
<mkmountpoint enable="1" remove="true" />
</pam_mount>
```

I had to add some mntoptions (empty require, all allow) and disable others (deny suid,dev and require nosuid,nodev). I am not really sure why I needed to reset the mntoptions in this way (the empty require), but I feel it is a bug in the parsing of the mntoptions.

My ~/.pam_mount.conf.xml was the same I used in 9.04.

Regards,

MV

---

### Post by varanasi on 2009-12-28
> **mvaldez said:**
> I modified only the /etc/security/pam_mount.conf.xml (didn't changed any file in /etc/pam.d/) 

Thanks very, very much for taking time to explain what you have done.  

I am now using Karmic but haven't yet succeeded.

When you say that you didn't change any file in /etc/pam.d, do you mean you left them as installed or as you had changed them for the earlier version?

---

### Post by dwroushey on 2010-03-02
I know this thread is a little old, but I thought I'd share my experience in case it's helpful.

**EDIT:** I'm using Ubuntu 9.10 (Karmic).

I'm going to assume you are already joined to the domain with likewise-open, but here is what I had to do in a nutshell:


[LIST=1]
[*]Install **smbfs** and **libpam-mount**. Open a terminal window and type:
```
sudo apt-get install smbfs libpam-mount
```
[*]Edit common-session:
```
sudo gedit /etc/pam.d/common-session
```
[*]Find the lines that look like this:
```
# and here are more per-package modules (the "Additional" block)
session    required    pam_unix.so
session    sufficient    pam_lsass.so
session    optional    pam_mount.so
session    optional            pam_ck_connector.so nox11
```
[*]The line with **pam_mount **needs to come before the line with **sufficient**. Swap them so it looks like:
```
# and here are more per-package modules (the "Additional" block)
session    required    pam_unix.so
session    optional    pam_mount.so
session    sufficient    pam_lsass.so
session    optional            pam_ck_connector.so nox11
```
[*]Save the file.
[*]Edit pam_mount.conf.xml. Here is mine as an example, but see manpages because it is really helpful ([http://manpages.ubuntu.com/manpages/karmic/man5/pam_mount.conf.5.html](http://manpages.ubuntu.com/manpages/karmic/man5/pam_mount.conf.5.html))
```
<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<!--
    See pam_mount.conf(5) for a description.
    
    This should go in /etc/security/
-->

<pam_mount>


        <!-- Volume definitions -->
<!-- mount studentH if you are not a member of faculty or staff -->
<volume options="user=%(DOMAIN_USER),dom=%(DOMAIN_NAME),setuids,acl"
        fstype="cifs"
        server="server_name"
        path="studenth/%(DOMAIN_USER)"
        mountpoint="~/%(DOMAIN_USER)"
> 
    <not><or>
        <sgrp>DOMAIN_NAME\faculty</sgrp>
        <sgrp>DOMAIN_NAME\staff</sgrp> 
    </or></not>
</volume>
<!-- mount employeeH if you are a member of faculty or staff -->
<volume options="user=%(DOMAIN_USER),dom=%(DOMAIN_NAME),setuids,acl"
        fstype="cifs"
        server="servername"
        path="employeeh/%(DOMAIN_USER)"
        mountpoint="~/%(DOMAIN_USER)"
> 
    <or>
        <sgrp>DOMAIN_NAME\Faculty</sgrp>
        <sgrp>DOMAIN_NAME\Staff</sgrp>
    </or>
</volume>
<!-- mount Linux if you are a member of CS-LinuxAdmins -->
<volume options="user=%(DOMAIN_USER),dom=%(DOMAIN_NAME),setuids,acl"
        fstype="cifs"
        server="servername"
        path="Linux"
        mountpoint="~/Linux"
    sgrp="DOMAIN_NAME\CS-LinuxAdmins"
/> 
<!-- mount Ldrive if you are a member of student or facutly-->
<volume options="user=%(DOMAIN_USER),dom=%(DOMAIN_NAME),setuids,acl"
        fstype="cifs"
        server="servername"
        path="courses"
        mountpoint="~/Courses"
>
    <or>
        <sgrp>DOMAIN_NAME\Students-A-F</sgrp>
        <sgrp>DOMAIN_NAME\Students-G-M</sgrp>
        <sgrp>DOMAIN_NAME\Students-N-S</sgrp>
        <sgrp>DOMAIN_NAME\Students-T-Z</sgrp>
        <sgrp>DOMAIN_NAME\Students-NES</sgrp>
        <sgrp>DOMAIN_NAME\Faculty</sgrp>
    </or>
</volume>

        <!-- pam_mount parameters: General tunables -->

<debug enable="0" />
<!--<luserconf name=".pam_mount.conf.xml" />-->

<!-- Note that commenting out mntoptions will give you the defaults.
     You will need to explicitly initialize it with the empty string
     to reset the defaults to nothing. -->
<!--
<mntoptions deny="suid,dev" />
<mntoptions allow="nosuid,nodev,loop,encryption,fsck,nonempty,allow_root,allow_other" />
<mntoptions allow="*" />
<mntoptions deny="*" />
-->
<mntoptions require="" />
<path>/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin</path>

<logout wait="0" hup="0" term="0" kill="0" />


        <!-- pam_mount parameters: Volume-related -->

<mkmountpoint enable="1" remove="true" />


</pam_mount>
```
[/LIST]
And then logout and log back in and you should be in business. Thats it, install 2 packages and modify 2 files. I didn't touch anything else.

I hope someone finds this helpful.

---

### Post by Ganapathy Santhanam on 2010-10-06
I'm using Ubuntu 10.04, i made all pam_mount configuration as above, still i dont see the mount.

pam_mount(pam_mount.c:314): pam_mount 1.32: entering auth stage
pam_mount(pam_mount.c:524): pam_mount 1.32: entering session stage
pam_mount(misc.c:38): Session open: (uid=617643651, euid=0, gid=0, egid=0)
pam_mount(pam_mount.c:583): **no volumes to mount**
command: [pmvarrun] [-u] [root] [-o] [1]
pam_mount(misc.c:38): set_myuid<pre>: (uid=617643651, euid=0, gid=0, egid=0)
pam_mount(misc.c:38): set_myuid<post>: **(uid=0, euid=0, gid=0, egid=0)**
pmvarrun(pmvarrun.c:248): parsed count value 1
pam_mount(pam_mount.c:424): pmvarrun says login count is 2
pam_mount(pam_mount.c:614): done opening session (ret=0)

any idea ?

---

### Post by steelsteel! on 2010-11-23
> **Ganapathy Santhanam said:**
> I'm using Ubuntu 10.04, i made all pam_mount configuration as above, still i dont see the mount.

pam_mount(pam_mount.c:314): pam_mount 1.32: entering auth stage
pam_mount(pam_mount.c:524): pam_mount 1.32: entering session stage
pam_mount(misc.c:38): Session open: (uid=617643651, euid=0, gid=0, egid=0)
pam_mount(pam_mount.c:583): **no volumes to mount**
command: [pmvarrun] [-u] [root] [-o] [1]
pam_mount(misc.c:38): set_myuid<pre>: (uid=617643651, euid=0, gid=0, egid=0)
pam_mount(misc.c:38): set_myuid<post>: **(uid=0, euid=0, gid=0, egid=0)**
pmvarrun(pmvarrun.c:248): parsed count value 1
pam_mount(pam_mount.c:424): pmvarrun says login count is 2
pam_mount(pam_mount.c:614): done opening session (ret=0)

any idea ?
That is exactly my problem. Plz Help soon!!!!!

My problem - as a post in here: [http://forum.ubuntuusers.de/post/2692319](http://forum.ubuntuusers.de/post/2692319)

---

### Post by steelsteel! on 2010-11-24
Man! Reading is gold!!!

Above was the solution, i didnt catch it in the beginning. The <volume>-Tag was faulty.
The right one is:
```
<volume options="user=%(DOMAIN_USER),dom=%(DOMAIN_NAME),setuids,acl"
        fstype="cifs"
        server="server_name"
        path="studenth/%(DOMAIN_USER)"
        mountpoint="~/%(DOMAIN_USER)"
> 

``` This solved my issue!

---

### Post by mvaldez on 2010-12-19
This is how we do it now using Ubuntu 10.04 to automatically mount our remote documents directory from a Linux server. As we no longer use Windows around here, most of us have replaced Samba mounts with SSHFS mounts, however the configuration is mostly the same.

The /etc/security/pam_mount.conf.xml file in my workstation is:

```

<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<pam_mount>
<debug enable="0" />
<luserconf name=".pam_mount.conf.xml" />
<mntoptions require="" />
<mntoptions allow="*" /> 
<path>/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin</path>
<logout wait="0" hup="0" term="0" kill="0" />
<mkmountpoint enable="1" remove="true" />
</pam_mount>

```

which the only thing it does is to define that each user has his own configuration file in their home directory as ~/.pam_mount.conf.xml. This allow each user to define if they use smbfs/cifs or sshfs and what directory to mount.

I didn't modify the /etc/pam.d/* files.

My ~/.pam_mount.conf.xml is:

```

<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE pam_mount SYSTEM "pam_mount.conf.xml.dtd">
<pam_mount>
<volume fstype="fuse" path="sshfs#mvaldez@wintermute:/home/mvaldez/SHARE" mountpoint="/home/mvaldez/Mis_Documentos" options="reconnect,idmap=user,password_stdin" />
</pam_mount>

```

In this example "mvaldez" is my username in the remote server, "wintermute" is the remote server name, "/home/mvaldez/SHARE" is the path in the remote server, and "/home/mvaldez/Mis_Documentos" is the path in my computer.

The "reconnect" option for SSHFS is very important if the computer is allowed to suspend; otherwise the mount won't try to reconnect after waking up. The password_stdin is needed so sshfs would accept the user password from stdin (I think this won't work with older versions of sshfs).

If I would use a Samba share, then I'd use:
```

<volume fstype="cifs" server="wintermute" path="mvaldez" mountpoint="/home/mvaldez/Mis_Documentos" options="iocharset=utf8,domain=biofmds,noperm" />

```


Just a few notes:

If the home directory for the user is encrypted with ecryptfs (I mean, not only a Private directory, but the whole user home directory) then PAM will try to mount the remote directories before unwrapping the ecryptfs mount password and it won't be able to read the ~/.pam_mount.conf.xml file. In that case you'll need to change the order of some items in the files /etc/pam.d/common-auth, common-session and common-session-noninteractive. You need to change the lines from:

```
auth   optional        pam_mount.so 
auth    optional        pam_ecryptfs.so unwrap
```

to:

```
auth    optional        pam_ecryptfs.so unwrap
auth    optional        pam_mount.so 
```

However, in that case you still have the problem that pam_mount will refuse to mount anything inside the decrypted directory. For users with this setup we had to mount in a special directory /home/share/username (and they have a bookmark in Nautilus for easy access).

Hope this helps anyone in a similar situation.

Regards, MV.

---

### Post by steelsteel! on 2010-12-20
Hello!

Interesting post. How do you manage to ger around the pam-unmount problem?
This means: pam-umount doesnt work with my settings under ubuntu while the user logs out?!

Greetings!

---

