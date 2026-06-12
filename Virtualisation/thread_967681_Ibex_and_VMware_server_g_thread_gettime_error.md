---
title: "Ibex and VMware server g_thread_gettime error"
date: 2008-11-02
forum: Virtualisation
---

### Post by GuruX on 2008-11-02
I have quite some trouble with VMware server and Ibex.

I first tried VMWare server 2.0 and it seemed to work fine. But I didn't like that stupid web interface, so I tried to download and compile VMware-server-client. But after installing it I got this error:

gustav@Laptop:~$ vmware
/usr/lib/vmware/bin/vmware: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
gustav@Laptop:~$ 

Ok, so I bitched around with it for a while. Didn't work out. Tried the .rpm for vmware-server-client with alient. But that didn't work out either.

So I downloaded 1.07 instead. Patched it with the neccesary patch and tried it. Same error now! Gah!

I have googled around some (g_thread_gettime), and it seems as if vmware expects an older glib with another path. I haven't really understood everything on the subject, so perhaps someone can help me undstand this.

This is probably the most helpful post, but I'm not sure I understand it.
[http://www.nabble.com/-Bug-543234--New:-vmware-crashes-while-loading-libgio-2.0.so.0-td18481777.html](http://www.nabble.com/-Bug-543234--New:-vmware-crashes-while-loading-libgio-2.0.so.0-td18481777.html)

edit: both versions have been installed from tarballs. vmware seems to be gone from the repos for ibex?

---

### Post by tstave on 2008-11-07
I have the same problem using Kubuntu and a 64 bit machine.

---

### Post by vodsdarov on 2008-11-07
Hello,
This bug was defined here:
[http://bugzilla.gnome.org/show_bug.cgi?id=543234]("http://bugzilla.gnome.org/show_bug.cgi?id=543234")

You may run in the console:
$ unset LD_LIBRARY_PATH
$ vmware

I had this same problem and now I've got vmware server 1.07 working again in ubuntu 8.10.
By now I created the following script:
```
#!/bin/bash
unset LD_LIBRARY_PATH
vmware
exit
```
And I point it inside the VMWare icon.

cheers!

---

### Post by turn1200 on 2008-11-07
> **vodsdarov said:**
> Hello,
This bug was defined here:
[http://bugzilla.gnome.org/show_bug.cgi?id=543234]("http://bugzilla.gnome.org/show_bug.cgi?id=543234")

You may run in the console:
$ unset LD_LIBRARY_PATH
$ vmware

I had this same problem and now I've got vmware server 1.07 working again in ubuntu 8.10.
By now I created the following script:
```
#!/bin/bash
unset LD_LIBRARY_PATH
vmware
exit
```
And I point it inside the VMWare icon.

cheers!

That didn't work for me.  I don't actually have anything set for LD_LIBRARY_PATH.

Anyone have any other suggestions?

---

### Post by turn1200 on 2008-11-10
I'm also on Kubuntu 64bit.

---

### Post by turn1200 on 2008-11-12
I fixed mine.

I had upgraded from the previous version.  Since I had my home partition separate I just decided to reinstall from scratch.  After doing that and creating a new user, this worked fine.  I'm not sure that the new user was necessary.  It may have worked otherwise or I may have been able to delete the ~/.vmware data.  I suspect the user wasn't necessary as this seems to be more of a library issue.

---

### Post by tvrtuscan on 2008-11-13
I still don't seem to be able to get rid of the g_thread_gettime error.  I've uninstalled vmware (using the uninstall script) and reinstalled a later version.

I started on version 1.0.6 and upgraded to 1.0.8.

I've tried the unset LD_LIBRARY_PATH but this seems to make no difference.

Here's the file it complains about:

```
ls -l /usr/lib32/libgio-2.0.so.0
lrwxrwxrwx 1 root root 22 2008-11-09 20:28 /usr/lib32/libgio-2.0.so.0 -> libgio-2.0.so.0.1800.2
```

and here's the contents of the library:

```
ldd /usr/lib32/libgio-2.0.so.0.1800.2
        linux-gate.so.1 =>  (0xf7fb3000)
        libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf7e7b000)
        libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf7e3d000)
        libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf7e37000)
        libselinux.so.1 => /lib32/libselinux.so.1 (0xf7e1d000)
        libc.so.6 => /lib32/libc.so.6 (0xf7cbf000)
        libpcre.so.3 => /lib32/libpcre.so.3 (0xf7c95000)
        libdl.so.2 => /lib32/libdl.so.2 (0xf7c91000)
        /lib/ld-linux.so.2 (0xf7fb4000)
```

Does anyone have any ideas or is anyone else experiencing the same problem?

---

### Post by Kiesel on 2008-11-16
i have the same problem with kubuntu 64 bit 8.10. tried also different combinations but it always says:
/usr/lib/vmware/bin/vmware: symbol lookup error: /usr/lib32/libgio-2.0.so.0: undefined symbol: g_thread_gettime

I tried to fix it by the links and ways posted here, but  as im not that much experienced i finally have to ask for help now.
So if somebody has another solution i would be really glad to hear it.

---

### Post by roxius on 2008-11-19
It worked for me using
[FONT="Courier New"]sudo vmware[/FONT]
in stead of
[FONT="Courier New"]vmware[/FONT]
it's only a half-baked solution, but maybe it works for you.

Cheers

---

### Post by greldinard on 2008-11-19
Using Kubuntu Intrepid Ibex 64-Bit, the same error occurs. Unfortunately none of the hints above worked for me. To me it seems to be a library version conflict. Does anybody know a workaround? Any help is appreciated!

My current workaround is: I installed the vmware-server-console on an Windows Terminalserver an use it with the seamless mode on my kubuntu box. Works fine, but isn't the way it's meant to be used :)

---

### Post by monarialx on 2008-11-20
I've replaced some libraries under /usr/lib/vmware-server-console/lib with older ones (taken from Hardy).
 - libglib-2.0.so.0
 - libgmodule-2.0.so.0
 - libgobject-2.0.so.0
 - libgthread-2.0.so.0
 - libXrender.so.1
 - libgio-2.0.so.0 <== NEW
 - libX11.so.6 <== NEW
I also patched /usr/lib/vmware-server-console/lib/wrapper-gtk24.sh to preload the NEW ones.

Now with
```
VMWARE_USE_SHIPPED_GTK="force" vmware-server-console
```
everything works again.

More details and files to download [here]("http://www.monarialx.it/en/node/121").

HTH

---

### Post by tvrtuscan on 2008-11-20
Thanks monarialx that worked for me!!! :)

Had to change it a little for vmware rather than vmware console but I'm back up and running again now.

Nice one

---

### Post by greldinard on 2008-11-28
monarialx - thank you very much!
You were patient enough to sort it all out.
It works fine!

---

### Post by willamowius on 2009-01-23
The fact the sudo vmware works led me to a much simpler solution (and safer than the sudo):

Its enough to just

unset GTK_RC_FILES
unset GTK2_RC_FILES

I put that into a little script that starts vmware and everything is jolly fine again.

---

### Post by tomeast on 2009-02-10
Thanks willamowius! You're solution worked for me.

---

### Post by drumz on 2009-02-14
None of the other solutions worked for me except running it with:

sudo vmware

Since that worked that indicated it was either a permission issue or environment.

In my home directory over time I eventually issued these two commands:

rm -rf .vmware
rm -rf .gnome*

That did it for me, I can run it without getting the g_thread_gettime error.  Please note that I'm a KDE user but I do have gnome installed so for those of you using Gnome you may just want to try removing the .vmware directory first, then if that doesn't work try moving the .gnome* directories someplace else.

Unfortunately I hadn't picked up on a permission error on my .vmware directory after running vmware with 'sudo vmware' so I went and just removed the .gnome* directories which may _not_ be necessary.....

---

### Post by rmi on 2009-03-04
roxius solution worked for me (sudo vmware).

therefore, the way to solve this problem, was to **change the permissions of that library to 666** (rw for everyone). note that **libgio-2.0.so.0 is probably just a symbolic link** to a different file, in my case libgio-2.0.so.0.1800.2, and the permissions of the file the link points to are the ones that have to be changed.

that means, a possible **permanent solution** for everyone with that library error is:
```

sudo su
cd /usr/lib32/
ls -la

```
and check what file libgio-2.0.so.0 points to, it will be called <lib> in the following
```

chmod 666 <lib>
exit

```
hope that helps

---

### Post by anandvaidya on 2009-03-23
Hi All,

I'm running Kubuntu Jaunty 9.04 Alpha6  + updates.

I have vmware-server 1.0.8. I have used vmware-update-2.6.27-5.5.7-2 package to complete vmware installation. I had the same problem reported here ( ie. /usr/lib/vmware/bin/vmware: symbol lookup error: /usr/lib32/libgio-2.0.so.0: undefined symbol: g_thread_gettime)

I followed monarialx method and works fine for me.

briefly:

I have my old 8.10 working copy of vmware in /mnt/usr/lib/vmware/

as root:
cd /usr/lib/vmware/lib/
rsync -av /mnt/usr/lib/vmware/lib/libglib-2.0.so.0 .
rsync -av /mnt/usr/lib/vmware/lib/libexpat.so.0 .


as user:
export VMWARE_USE_SHIPPED_GTK=force; vmware

it spews tons of errors (ld.so complaining, but UI starts up)

I just wanted this to be documented here for Jaunty Jackalope 9.04

---

### Post by locutus42 on 2009-05-06
> **anandvaidya said:**
> Hi All,
<clip>
briefly:

I have my old 8.10 working copy of vmware in /mnt/usr/lib/vmware/

as root:
cd /usr/lib/vmware/lib/
rsync -av /mnt/usr/lib/vmware/lib/libglib-2.0.so.0 .
rsync -av /mnt/usr/lib/vmware/lib/libexpat.so.0 .


as user:
export VMWARE_USE_SHIPPED_GTK=force; vmware

it spews tons of errors (ld.so complaining, but UI starts up)

I just wanted this to be documented here for Jaunty Jackalope 9.04

You are da man!  worked great and without any spewing errors for the vmware-server-console v1.0.4. FWIW, after seeing what Vmware v2 is like, I'll do what it takes to keep the 1.x stuff running.

Thanks tons.

---

