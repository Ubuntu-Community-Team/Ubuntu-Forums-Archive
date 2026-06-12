---
title: "gksu gives quirky error"
date: 2014-05-20
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-05-20
Installed gksu and at first would not accept my password. Rebooted and now I get this error window and these messages in terminal, but it still works..

```

ventrical@ventrical-MS-7798:~$ gksu nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:2410): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs


(nautilus:2410): GLib-CRITICAL **: Source ID 172 was not found when attempting to remove it

(nautilus:2410): GLib-CRITICAL **: Source ID 173 was not found when attempting to remove it

(nautilus:2410): GLib-CRITICAL **: Source ID 174 was not found when attempting to remove it
ventrical@ventrical-MS-7798:~$ 




```

 .. this all on a fresh install from iso.

---

### Post by philinux on 2014-05-20
The devs have been quoted as saying in the recent past not to use stuff like gksu nautilus. Not sure what exactly they do recommend. Maybe sudo nano or something else.

---

### Post by ventrical on 2014-05-20
I basically use gksu nautilus  just to edit .conf files .. etc. Nautilus provides and easier "look" about . Using just 'gedit' is kind of tweaky .. but I'll get used to it.

Thanks.

Regards..

---

### Post by grahammechanical on 2014-05-20
I get those messages after I close nautilus loaded by gksu

> graham@Sdb8-Roll-Dev:~$ gksu nautilus


(nautilus:3899): GLib-CRITICAL **: Source ID 116 was not found when attempting to remove it


(nautilus:3899): GLib-CRITICAL **: Source ID 117 was not found when attempting to remove it


(nautilus:3899): GLib-CRITICAL **: Source ID 118 was not found when attempting to remove it

gksu has been depreciated and that may mean then no one is bothered about fixing things. We are supposed to use polkit (PolicyKit)

```
pkexec program
```

But first we need to define the policy. I did a little bit of experimentation with 2 cycles ago but it seemed too much like work just to set up Gedit and Nautilus with pkexec. I will review my studies and post back.

Regards.

---

### Post by zika on 2014-05-20
> **grahammechanical said:**
> I get those messages after I close nautilus loaded by gksu


gksu has been depreciated and that may mean then no one is bothered about fixing things. We are supposed to use polkit (PolicyKit)

```
pkexec program
```

But first we need to define the policy. I did a little bit of experimentation with 2 cycles ago but it seemed too much like work just to set up Gedit and Nautilus with pkexec. I will review my studies and post back.

Regards.
Or```
/usr/bin/sudo -H *program*
```...

---

### Post by grahammechanical on 2014-05-20
Ok here goes. And I am using a script for gedit that someone posted in this section about a year ago and then I modified it to work with nautilus. This I think is the Ubuntu developer official method.

Look in /usr/share/polkit-1/actions to see official PolicyKit policies. We need to create similar policies of the same pattern. So, for Gedit we create /usr/share/polkit-1/actions/com.ubuntu.gedit.policy

And here is the policy as given by someone a year ago and  it works.

> <?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>
  <vendor>gedit</vendor>
  <vendor_url>gedit</vendor_url>
  <icon_name>accessories-text-editor</icon_name>
  <action id="org.freedesktop.policykit.pkexec.gedit">
   <description>Run "gedit"</description>
   <message>Authentication is required to run Text Editor</message>
   <defaults>
     <allow_any>auth_admin</allow_any>
     <allow_inactive>auth_admin</allow_inactive>
     <allow_active>auth_admin</allow_active>
   </defaults>
     <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/gedit</annotate>
     <annotate key="org.freedesktop.policykit.exec.allow_gui">true</annotate>
   </action>  
</policyconfig>


```
pkexec gedit
```

I have modified that script replacing all use of "gedit" with "nautilus" and created /usr/share/polkit-1/actions/com.ubuntu.nautilus.policy and that works also of a kind.

```
pkexec nautilus
```

does load nautilus with sudo/root privileges but it throws these errors in the terminal

> (nautilus:4861): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


(nautilus:4861): GLib-CRITICAL **: Source ID 112 was not found when attempting to remove it


(nautilus:4861): GLib-CRITICAL **: Source ID 113 was not found when attempting to remove it


(nautilus:4861): GLib-CRITICAL **: Source ID 114 was not found when attempting to remove it



But then again gksu is not so clean either. As I said it is a little too much like work to do this for every install I am testing. Far easier to install gksu.

EDIT: I am guessing that part of the reason for the nautilus error messages is the wrong path. /usr/bin/gedit is correct for Gedit but /user/bin/nautilus is not correct for Nautilus. At least that is what I am guessing.

Regards

---

### Post by ventrical on 2014-05-20
> **zika said:**
> Or```
/usr/bin/sudo -H *program*
```...

```

ventrical@ventrical-MS-7798:~$ /usr/bin/sudo -H nautilus
[sudo] password for ventrical: 

(nautilus:3157): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:3157): GLib-CRITICAL **: Source ID 99 was not found when attempting to remove it

(nautilus:3157): GLib-CRITICAL **: Source ID 100 was not found when attempting to remove it

(nautilus:3157): GLib-CRITICAL **: Source ID 101 was not found when attempting to remove it
ventrical@ventrical-MS-7798:~$ 

```

I got the same thing but with different ID numbers.

---

### Post by ventrical on 2014-05-20
> **grahammechanical said:**
> 
But then again gksu is not so clean either. As I said it is a little too much like work to do this for every install I am testing. Far easier to install gksu.


My feelings exactly.

Thanks for the research on that. 

Regards..

---

### Post by ventrical on 2014-05-20
I am *NOT* suggesting to anyone to try this.  I was just able to set my permissions to Group <username> on selected files, ie; <NetworkManager.conf> so as I can easily edit it without the harang of using gksu or other. In early development I think this is ok as some files may have to be edited often and can always be reset.

Regards..

---

### Post by zika on 2014-05-20
What do You all get (any changes in reported behaviour) if You beforehand remove ~/.gksu.lock (if the file exists whatsoever)...?

---

### Post by ventrical on 2014-05-20
> **zika said:**
> What do You all get (any changes in reported behaviour) if You beforehand remove ~/.gksu.lock (if the file exists whatsoever)...?

Thats a little over my head .. you would have to walk me through it. :)

Regards..

---

### Post by zika on 2014-05-20
```
rm ~/.gksu.lock
[COLOR=#a52a2a]gksu nautilus[/COLOR]
```
This ([COLOR=#a52a2a]red[/COLOR]) should not be done from terminal because that is well known issue that could cause permission disorder as this was a problem all the time I've been using Ubuntu and *nix whatsoever... That is the reason to use sudo with aforementioned switch... So, all this that is reason for this thread could be a superposition of known &#8222;ilegagal&#8220; usage of GUI command from CLI and some &#8222;new&#8220; bug that creeped from under the rug...

---

### Post by ventrical on 2014-05-20
It worked very smoothly ,(no pop-ups), but still got 'not found' errors.

```

ventrical@ventrical-MS-7798:~$ rm ~/.gksu.lock
ventrical@ventrical-MS-7798:~$ /usr/bin/sudo -H nautilus
[sudo] password for ventrical: 

(nautilus:2757): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:2757): GLib-CRITICAL **: Source ID 104 was not found when attempting to remove it

(nautilus:2757): GLib-CRITICAL **: Source ID 105 was not found when attempting to remove it

(nautilus:2757): GLib-CRITICAL **: Source ID 106 was not found when attempting to remove it
ventrical@ventrical-MS-7798:~$ 


```

EDIT:

 I am just curious as to if :

```
 rm ~/.gksu.lock


```

can be reversed back to original (and how to).

Thanks..

---

### Post by zika on 2014-05-20
~/.gksu.lock is an empty file that is just a marker (ergo .lock in its name) so```
touch ~/.gksu.lock
```shoud be enough to regenerate it but I do not recommend that since that file should not be present if no application is active that could have made it....
Back to the main thing: does```
gksu nautilus
```work from GUI (since it should not be used, as written as much as above and much more (detailed and explained) through whole of the net)?
Do You have samba installed? Are groups for samba (usershare) properly set?
What```
ls -alt /var/lib/samba
ls -alt /var/lib/samba/usershares
```gives?

---

### Post by philinux on 2014-05-20
Not at home.  Thoughts

what does sudo -i then run nautilus give. Errors or not?

---

### Post by zika on 2014-05-20
I do not have time to write about this in detail (#SerbiaFloods) so I'll just quote:
> 
[TABLE]
[TR]
[TD="class: votecell"]     60     down vote                accepted[/TD]
[TD="class: answercell"]                  Taken from [here]("https://help.ubuntu.com/community/RootSudo#Graphical_sudo"):[INDENT]   You should **never** use normal sudo to start graphical applications as   root. You should use gksudo (kdesudo on Kubuntu) to run such programs.   gksudo sets HOME=/root, and copies .Xauthority to a tmp directory.   This prevents files in your home directory becoming owned by root.
 [/INDENT]
Please note that this is primarily about *configuration files*. If you run Nautilus as root, even with gksu/gksudo, and you create a file or folder anywhere with it (including in your home directory), that file or folder will be owned by root. But if you run Nautilus (or most other graphical applications) as root with sudo, they may save their *configuration files* in your home directory (rather than root's home directory). Those configuration files may be owned by root  and inaccessible when you're not running as root, which can severely  mess up your settings, and may even keep some applications from working  altogether.
  The solution, once you have made this mistake, is to find the configuration files and delete them or [chown]("http://manpages.ubuntu.com/manpages/precise/en/man1/chown.1.html") them back to belonging your non-root user. Many such files start with a . or are contained in a directory that starts with a .. Some are located inside the .config folder in your home directory. To see files and folders that start with a . in Nautilus, press Ctrl+H (this *shows hidden files*.) To see them with [ls]("http://manpages.ubuntu.com/manpages/precise/en/man1/ls.1.html"), use the -a (or -A) flag.
  To find if there are files not owned by you in your home directory, you can use the following command in a terminal: 
  find $HOME -not -user $USER -exec ls -lad {} \;
  which will list all files under the home directory not owned by the user.[/TD]
[/TR]
[/TABLE]
([http://askubuntu.com/a/11766](http://askubuntu.com/a/11766))
So either back to original question about **gksu** and **nautilus** or to usage of **sudo** with ***-H*** switch...
Vanilla **sudo** should not be used with **nautilus** (or _***any other GUI app.***_). Over&out... ;)

---

### Post by grahammechanical on 2014-05-20
I have just found .gksu.lock in my home folder. The home folder we access through "computer". /home/username/ It is indeed an empty file. I have deleted it and run gksu_do_ nautilus and I still get the GLib-CRITICAL error messages and .gksu.lock is recreated.

Being an ignorant tester I guess this file is used to prevent more than one appplication/user modifying these files at a time. And sudo -i nautilus gives this when nautilus opens 

> (nautilus:4519): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

and this after nautilus is closed

> (nautilus:4519): GLib-CRITICAL **: Source ID 115 was not found when attempting to remove it


(nautilus:4519): GLib-CRITICAL **: Source ID 116 was not found when attempting to remove it


(nautilus:4519): GLib-CRITICAL **: Source ID 117 was not found when attempting to remove it

Now, I am getting bored.

---

### Post by ventrical on 2014-05-20
> **zika said:**
> ~/.gksu.lock is an empty file that is just a marker (ergo .lock in its name) so```
touch ~/.gksu.lock
```shoud be enough to regenerate it but I do not recommend that since that file should not be present if no application is active that could have made it....
Back to the main thing: does```
gksu nautilus
```work from GUI (since it should not be used, as written as much as above and much more (detailed and explained) through whole of the net)?
Do You have samba installed? Are groups for samba (usershare) properly set?
What```
ls -alt /var/lib/samba
ls -alt /var/lib/samba/usershares
```gives?

 Ok.. this time it was different. After entering in 'gksu nautilus' there were no errors, only after I exited from nautilus.

Also .. I think I need to learn a little bit about samba (my bad not knowing this  by now)

```

ventrical@ventrical-MS-7798:~$ gksu nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:2831): GLib-CRITICAL **: Source ID 99 was not found when attempting to remove it

(nautilus:2831): GLib-CRITICAL **: Source ID 100 was not found when attempting to remove it

(nautilus:2831): GLib-CRITICAL **: Source ID 101 was not found when attempting to remove it
ventrical@ventrical-MS-7798:~$ ls -alt /var/lib/samba
total 12
drwxr-xr-x 68 root root 4096 May 20 12:50 ..
drwxr-xr-x  3 root root 4096 May 14 03:33 .
drwxr-xr-x  2 root root 4096 Apr 29 20:23 private
ventrical@ventrical-MS-7798:~$ ls -alt /var/lib/samba/usershares
ls: cannot access /var/lib/samba/usershares: No such file or directory
ventrical@ventrical-MS-7798:~$ 

```

Thanks again..

---

### Post by ventrical on 2014-05-20
> **grahammechanical said:**
> I have just found .gksu.lock in my home folder. The home folder we access through "computer". /home/username/ It is indeed an empty file. I have deleted it and run gksu_do_ nautilus and I still get the GLib-CRITICAL error messages and .gksu.lock is recreated.

Being an ignorant tester I guess this file is used to prevent more than one appplication/user modifying these files at a time.

 I am not 100% sure but I think this is a samba issue and me not knowing how to use/install it.  I did at one time but I have been just ignoring it and I mostly forget .. so I am going to try and learn to install that and play around with that a bit and see what happens about those errors, time permitting of course.

Regards..

---

### Post by ventrical on 2014-05-20
I went to /computer/ and right clicked, then, properties and user shares and I chose to install samba.

It made some difference with those error messages.

```

ventrical@ventrical-MS-7798:~$ ls -alt /var/lib/samba
total 1364
drwxr-xr-x  3 root root         4096 May 20 16:07 private
-rw-------  1 root root       528384 May 20 16:07 registry.tdb
-rw-------  1 root root       421888 May 20 16:07 account_policy.tdb
drwxr-xr-x  5 root root         4096 May 20 16:07 .
-rw-------  1 root root          696 May 20 16:07 group_mapping.tdb
-rw-------  1 root root       421888 May 20 16:07 share_info.tdb
drwxrwx--T  2 root sambashare   4096 May 20 16:07 usershares
drwxr-xr-x 10 root root         4096 May 20 16:07 printers
drwxr-xr-x 68 root root         4096 May 20 12:50 ..
ventrical@ventrical-MS-7798:~$ ls -alt /var/lib/samba/usershares
total 8
drwxr-xr-x 5 root root       4096 May 20 16:07 ..
drwxrwx--T 2 root sambashare 4096 May 20 16:07 .
ventrical@ventrical-MS-7798:~$ gksu nautilus

(nautilus:2497): GLib-CRITICAL **: Source ID 101 was not found when attempting to remove it

(nautilus:2497): GLib-CRITICAL **: Source ID 102 was not found when attempting to remove it
s
ventrical@ventrical-MS-7798:~$ 

```

also, during the process it wanted to install a PAM file but it would not let me install (ghost vanilla file).

---

### Post by cariboo on 2014-05-20
> **ventrical said:**
> also, during the process it wanted to install a PAM file but it would not let me install (ghost vanilla file).

That seems to be a bug with the file-sharing installation process. you can install libpam-smbpass manually.

---

### Post by ventrical on 2014-05-20
> **cariboo907 said:**
> That seems to be a bug with the file-sharing installation process. you can install libpam-smbpass manually.

After installing that I have some of the old errors back.

```

ventrical@ventrical-MS-7798:~$ gksu nautilus

(nautilus:3818): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(nautilus:3818): GLib-CRITICAL **: Source ID 97 was not found when attempting to remove it

(nautilus:3818): GLib-CRITICAL **: Source ID 98 was not found when attempting to remove it

(nautilus:3818): GLib-CRITICAL **: Source ID 99 was not found when attempting to remove it
ventrical@ventrical-MS-7798:~$ 


```

---

### Post by ventrical on 2014-05-20
I removed libpam-smbpass and got rid of that first error.

```

ventrical@ventrical-MS-7798:~$ gksu nautilus

(nautilus:2465): GLib-CRITICAL **: Source ID 97 was not found when attempting to remove it

(nautilus:2465): GLib-CRITICAL **: Source ID 98 was not found when attempting to remove it

(nautilus:2465): GLib-CRITICAL **: Source ID 99 was not found when attempting to remove it
ventrical@ventrical-MS-7798:~$ 



```

---

### Post by Sworddragon on 2014-05-21
I'm getting a similar error with the same effects and have opened a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/1321704](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/1321704)

I'm also assuming this error comes from upgrading to the Linux Kernel 3.15.x as I read something that it integraded some mysterious POSIX locks. Can you downgrade to an older kernel and check if this fixes the error for you?


Edit: I have now downgraded the Linux Kernel and it does indeed fix the issue so this maybe works for you too.

---

### Post by ventrical on 2014-05-21
Ok .. I'll try to downgrade after what this new kernel coughs up.

```

ventrical@ventrical-MS-7798:~$ gksu nautilus

** (gksu:2481): CRITICAL **: fcntl error

** (gksu:2481): WARNING **: Lock taken by pid: -1. Exiting.
ventrical@ventrical-MS-7798:~$ 


```

---

### Post by ventrical on 2014-05-21
> **Sworddragon said:**
> I'm getting a similar error with the same effects and have opened a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/1321704](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/1321704)

I'm also assuming this error comes from upgrading to the Linux Kernel 3.15.x as I read something that it integraded some mysterious POSIX locks. Can you downgrade to an older kernel and check if this fixes the error for you?


Edit: I have now downgraded the Linux Kernel and it does indeed fix the issue so this maybe works for you too.


Yep .. works here . 

Me tooed that bug also. :)

Thnx.

EDIT:

Just to clarifiy I used GRuB and chose 3.13.0-24 kernel. Not downgraded kernel.

---

### Post by zika on 2014-05-21
> **Sworddragon said:**
> I'm getting a similar error with the same effects and have opened a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/1321704](https://bugs.launchpad.net/ubuntu/+source/gksu/+bug/1321704)

I'm also assuming this error comes from upgrading to the Linux Kernel 3.15.x as I read something that it integraded some mysterious POSIX locks. Can you downgrade to an older kernel and check if this fixes the error for you?


Edit: I have now downgraded the Linux Kernel and it does indeed fix the issue so this maybe works for you too.No need to downgrade, kernels can coexist...

---

### Post by philinux on 2014-05-21
I've subscribed to the bug. Bet anything the answer answer comes back saying don't use gksu anything. Or not recommended.

---

### Post by ventrical on 2014-05-21
> **philinux said:**
> I've subscribed to the big. Bet anything the answer answer comes back saying don't use gksu anything. Or not recommended.


 I have one machine that is so fast that it doesn't matter about how much breakage I get.  I just re-install over borked. But, without gksu  it makes for a lot of extra work when one is dynamically  testing and trying to edit .conf files on the fly. Less downtime equals more fun :)

---

### Post by Alan F on 2014-05-21
Ubuntu devs will not even allow you to move the window controls to the right. 

Do you really expect them to make it easy to edit .conf files?

---

### Post by zika on 2014-05-21
Where does difficulty in changing .conf files reside?
I do change such files a lot each and every day...
What am I missing?

---

### Post by ventrical on 2014-05-21
It is not a difficulty. It is just that we (I) have to drop to root or use gksu (or whatever other) to be able to save those .conf files that belong to  root. For example , when switching  back and forth with Mir and xorg the only way to edit is to toggle in root (edit out unity line .. etc, ). So .. not difficulty (I did not say difficulty) just downtime. (I did say downtime).

---

### Post by ventrical on 2014-05-21
> **Alan F said:**
> Ubuntu devs will not even allow you to move the window controls to the right. 

Do you really expect them to make it easy to edit .conf files?

No .. I do not have that expectation . However as a *voulnteer* tester I like to move fast as possible and contribute somthing, at least, to help out. Fanaggling with permissions as such to edit .conf files (and with Mir and Unity8 testing) it causes a lot of downtime for me. Unless (I am sure) I can just assign those files to my username group and not #root.

Just a side note: I totally understand about how delicate #root is and that is main security for Ubuntu etc.. but as  a tester I am not worried about loosing an install. Thats the way the cookie crumbles. I am just tryin to streamline my testing techniques. So I am always on the lookout for tips and work-a-rounds.

---

### Post by zika on 2014-05-21
> **ventrical said:**
> It is not a difficulty. It is just that we (I) have to drop to root or use gksu (or whatever other) to be able to save those .conf files that belong to  root. For example , when switching  back and forth with Mir and xorg the only way to edit is to toggle in root (edit out unity line .. etc, ). So .. not difficulty (I did not say difficulty) just downtime. (I did say downtime).Simply said (not having time to elaborate (#SerbiaFlood)): wrong...

> **ventrical said:**
> No .. I do not have that expectation . However as a *voulnteer* tester I like to move fast as possible and contribute somthing, at least, to help out. Fanaggling with permissions as such to edit .conf files (and with Mir and Unity8 testing) it causes a lot of downtime for me. Unless (I am sure) I can just assign those files to my username group and not #root.

Just a side note: I totally understand about how delicate #root is and that is main security for Ubuntu etc.. but as  a tester I am not worried about loosing an install. Thats the way the cookie crumbles. I am just tryin to streamline my testing techniques. So I am always on the lookout for tips and work-a-rounds.Simply said (not having time to elaborate (#SerbiaFlood)): wrong...

Simply make a plan what You really want to test and make appropriate (user)groups, differentiate what needs to be tested as (let me say) &#8222;ordinary&#8220; user and what can be done from elevated permissions user (did not write &#8222;root&#8220;)...
You'll be surprised what  (lot of stuff) can be tested with so little change in (those You, obviously like so much) .conf (and similar) files... You're making joke with all the testing effort we've had here for years by talking about &#8222;downtime&#8220; for editing .conf-like files...

Please do elaborate on &#8222;Your testing techniques&#8220;. Testing Ubuntu is using it in everyday life and working on it not creating situations (almost)noone will ever get into etc...

Yes, I'm very worried about loosing install (I do not call myself &#8222;tester&#8220;, just ordinary user, so that might be the cause od our difference) and I do try to use one install as long as possible (even though i do have backup) and this install (I'm writing from) is quite an old one... Been through lot of stuff and bear some bruises but...

Ubuntu is being tested for everyday and serious use, I presume, and I might be wrong in that belief...

Note: Strictly speaking this post of mine is a total offtopic in this thread but I do not feel responsible as I did not start it. I just feel responsible for not being able to control my urge to answer and I do apologize for that...

Over & out...

---

### Post by ventrical on 2014-05-21
> **zika said:**
> You're making joke with all the testing effort we've had here for years by talking about „downtime“ for editing .conf-like files...


  Here we go again...

  I always hope my contributons help refine ubuntu, not define the contributions of the end_users here. We are asked and recruited to give our best .. and I do. I don't make any jokes about it.  Sorry about your floods but world disasters happen world wide, not just Serbia. (I live in Tornado alley) .

As a student of computer science from noted University of Windsor Canada many years ago it was drilled into me about writing efficient programs and that downtime was a thing to be avoided. Any kind of downtime. As anyone here can see there is this football back n' forth with gksu, sudo -H and policy-kit, which is secure, which is not etc.. These  problem messages in terminal with gksu have been around for some time. At least since I started using it. Mark Shuttleworth proclaims that he wants to cut away this stuff, this dross and make it easier for normal users.  So we have to report these things, do we not? We have to explore these things, elst,  why are we here then?  I ask, I listen and then I try different things suggested. I have old installs and new installs. I don't know what this has to do with the discussion.

I am slighted that you would make a comment directed at me as to 'making  joke' about testing effort. You are wrong and it is not true.

Best Regards..

---

### Post by cariboo on 2014-05-21
With that, this thread needs to be closed. Let's not bring personalities into the conversation. Thread closed

---

