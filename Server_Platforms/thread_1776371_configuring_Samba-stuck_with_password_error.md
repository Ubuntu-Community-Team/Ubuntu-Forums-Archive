---
title: "configuring Samba-stuck with password error"
date: 2011-06-06
forum: Server Platforms
---

### Post by smcrossman on 2011-06-06
I'm tired so hopefully this is the right place and I will make sense!

I have installed and configured Samba on 2 of my 3 computers. Now I am going through the testing on one of them...in the process of trying to work out usernames/passwords, etc. Since this is like Greek to me it's going slowly.  I have gotten to step 7 in the Tests portion of 

[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html)

I am getting

[I]Server requested plaintext password but 'client plaintext auth' is disabled
session setup failed: SUCCESS - 0[/I]

A brief search of the forums showed an older thread (circa 2009) with similar issue, but it's remaining gibberish to my tired brain.

I have run and copied testparm -v, but it's 9 pages in the text document so I'm not going to try to guess what I need to post right now.

For when I get up and can think again....***what more information can I give so someone can help me figure out how to tweak the security or password settings to move on through this process***? 

I've already bookmarked 

[http://samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html](http://samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html)

since I suspect I'm going to be needing it.

I know I have some issues to resolve as I add users since my 3 computers are:  in Windows:  Gateway, (Win 7 64 bit) users SMCrossman, Suzanna; Dell (Win 7 32 bit), user suzanna aka zan (windows doesn't take name changes well so it isn't consistent); in Ubuntu: suzanna on suzanna-gateway; suzanna on suzanna-dell; and suzanna on suzanna-desktop (Ubuntu only).  My goal WAS just to keep things clear and consistent (passwords are the same for users per OS as well) until I had some idea how naming worked in whatever networking/sharing system I ended up using. Now that I'm actually starting the programming I'll need to get things a little better differentiated. Tips/suggestions on that would also be appreciated.

---

### Post by smcrossman on 2011-06-06
Okay...no responses? Am I posting in the wrong place? I could really use just a little guidance to push past this error message.....

---

### Post by capscrew on 2011-06-06
> **smcrossman said:**
> Okay...no responses? Am I posting in the wrong place? I could really use just a little guidance to push past this error message.....

Hey... Some of use are just waking up too.  :-)

I would recommend logins for the users in the network be the same on all hosts including the Ubuntu host that is the Samba server. In addition there should be a Samba user created on the Ubuntu host  using *smbpasswd -a*.

Are you aware that the information that you linked to is inaccurate in some ways for a Debian/Ubuntu install?

---

### Post by Morbius1 on 2011-06-06
> [I]Server requested plaintext password but 'client plaintext auth' is disabled
session setup failed: SUCCESS - 0[/I]You can also get that error if you have:
> encrypt passwords = NoIf that's the case set it to Yes and restart samba:
```
 sudo service smbd restart
```> I have run and copied testparm -v, but it's 9 pages in the text document  so I'm not going to try to guess what I need to post right now.Then don't run "-v" - that will produce more settings than most humans have ever seen. Just run with a plain "-s" instead:
```
testparm -s
```
The output of that is small enough to post.

---

### Post by smcrossman on 2011-06-06
Okay, well I spent time today confirming that my 2 computers were pinging each other and identifying each other properly. Made a few more small changes to the smb.conf hoping I might get lucky (little things I missed earlier like valid users....)

I did have encrypt passwords=no, so I changed that and ran testparm.  I then did sudo restart nmbd, and restart smbd. Did the smbclient test. Got slightly different error ... what I did and the command you gave me weren't really the same so I did the command you gave me and got this:

[INDENT][I][SIZE=1]root@suzanna-dell:/home/suzanna# sudo service smbd restart[/SIZE]
[SIZE=1]smbd start/running, process 8563[/SIZE]
[SIZE=1]root@suzanna-dell:/home/suzanna# smbclient //suzanna-dell/tmp[/SIZE]
[SIZE=1]Enter root's password: [/SIZE]
[SIZE=1]Domain=[HOME] OS=[Unix] Server=[Samba 3.5.8][/SIZE]
[SIZE=1]tree connect failed: NT_STATUS_LOGON_FAILURE[/SIZE]
[SIZE=1]root@suzanna-dell:/home/suzanna# [/SIZE][/I]
[/INDENT]
Better...looks like the password is working now, but ?  So just to be sure I went to the gateway logged out of Ubuntu and booted up Windows 7. Did a quick ping to make sure it was on the network (having issues with the wireless adaptor). Then tried again.

here is the testparm output (hopefully you'll see something I have no idea what I'm looking at)
[FONT=System][SIZE=1]
[/SIZE][/FONT][INDENT][FONT=System][SIZE=1]root@suzanna-dell:/home/suzanna# pdbedit -L[/SIZE][/FONT]
[FONT=System][SIZE=1]nobody:65534:nobody[/SIZE][/FONT]
[FONT=System][SIZE=1]suzanna:1000:Suzanna Crossman[/SIZE][/FONT]
[FONT=System][SIZE=1]root@suzanna-dell:/home/suzanna# testparm -s /etc/samba/smb.conf[/SIZE][/FONT]
[FONT=System][SIZE=1]Load smb config files from /etc/samba/smb.conf[/SIZE][/FONT]
[FONT=System][SIZE=1]rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)[/SIZE][/FONT]
[FONT=System][SIZE=1]Processing section "[homes]"[/SIZE][/FONT]
[FONT=System][SIZE=1]Processing section "[profiles]"[/SIZE][/FONT]
[FONT=System][SIZE=1]Global parameter username map found in service section![/SIZE][/FONT]
[FONT=System][SIZE=1]Global parameter guest account found in service section![/SIZE][/FONT]
[FONT=System][SIZE=1]Processing section "[printers]"[/SIZE][/FONT]
[FONT=System][SIZE=1]Processing section "[print$]"[/SIZE][/FONT]
[FONT=System][SIZE=1]Processing section "[suzanna]"[/SIZE][/FONT]
[FONT=System][SIZE=1]Processing section "[Desktop]"[/SIZE][/FONT]
[FONT=System][SIZE=1]Processing section "[Pictures]"[/SIZE][/FONT]
[FONT=System][SIZE=1]Processing section "[File System]"[/SIZE][/FONT]
[FONT=System][SIZE=1]lp_bool(root, admin, suzanna): value is not boolean![/SIZE][/FONT]
[FONT=System][SIZE=1]Processing section "[share]"[/SIZE][/FONT]
[FONT=System][SIZE=1]Processing section "[tmp]"[/SIZE][/FONT]
[FONT=System][SIZE=1]Loaded services file OK.[/SIZE][/FONT]
[FONT=System][SIZE=1]Server role: ROLE_STANDALONE[/SIZE][/FONT]
[FONT=System][SIZE=1][global][/SIZE][/FONT]
[FONT=System][SIZE=1]    workgroup = HOME[/SIZE][/FONT]
[FONT=System][SIZE=1]    server string = %h server (Samba, Ubuntu)[/SIZE][/FONT]
[FONT=System][SIZE=1]    map to guest = Bad User[/SIZE][/FONT]
[FONT=System][SIZE=1]    obey pam restrictions = Yes[/SIZE][/FONT]
[FONT=System][SIZE=1]    pam password change = Yes[/SIZE][/FONT]
[FONT=System][SIZE=1]    passwd program = /usr/bin/passwd %u[/SIZE][/FONT]
[FONT=System][SIZE=1]    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .[/SIZE][/FONT]
[FONT=System][SIZE=1]    username map = /etc/samba/smbusers[/SIZE][/FONT]
[FONT=System][SIZE=1]    unix password sync = Yes[/SIZE][/FONT]
[FONT=System][SIZE=1]    syslog = 0[/SIZE][/FONT]
[FONT=System][SIZE=1]    log file = /var/log/samba/log.%m[/SIZE][/FONT]
[FONT=System][SIZE=1]    max log size = 1000[/SIZE][/FONT]
[FONT=System][SIZE=1]    dns proxy = No[/SIZE][/FONT]
[FONT=System][SIZE=1]    usershare allow guests = Yes[/SIZE][/FONT]
[FONT=System][SIZE=1]    panic action = /usr/share/samba/panic-action %d[/SIZE][/FONT]
[FONT=System][SIZE=1]    valid users = @smbusers, suzanna[/SIZE][/FONT]
[FONT=System][SIZE=1]    guest ok = Yes[/SIZE][/FONT]

[FONT=System][SIZE=1][homes][/SIZE][/FONT]
[FONT=System][SIZE=1]    comment = Home Directories[/SIZE][/FONT]
[FONT=System][SIZE=1]    read only = No[/SIZE][/FONT]
[FONT=System][SIZE=1]    create mask = 0700[/SIZE][/FONT]
[FONT=System][SIZE=1]    directory mask = 0750[/SIZE][/FONT]

[FONT=System][SIZE=1][profiles][/SIZE][/FONT]
[FONT=System][SIZE=1]    comment = Users profiles[/SIZE][/FONT]
[FONT=System][SIZE=1]    path = /home/samba/profiles[/SIZE][/FONT]
[FONT=System][SIZE=1]    create mask = 0600[/SIZE][/FONT]
[FONT=System][SIZE=1]    directory mask = 0700[/SIZE][/FONT]
[FONT=System][SIZE=1]    browseable = No[/SIZE][/FONT]

[FONT=System][SIZE=1][printers][/SIZE][/FONT]
[FONT=System][SIZE=1]    comment = All Printers[/SIZE][/FONT]
[FONT=System][SIZE=1]    path = /var/spool/samba[/SIZE][/FONT]
[FONT=System][SIZE=1]    create mask = 0700[/SIZE][/FONT]
[FONT=System][SIZE=1]    printable = Yes[/SIZE][/FONT]
[FONT=System][SIZE=1]    browseable = No[/SIZE][/FONT]

[FONT=System][SIZE=1][print$][/SIZE][/FONT]
[FONT=System][SIZE=1]    comment = Printer Drivers[/SIZE][/FONT]
[FONT=System][SIZE=1]    path = /var/lib/samba/printers[/SIZE][/FONT]
[FONT=System][SIZE=1]    write list = root, @lpadmin[/SIZE][/FONT]

[FONT=System][SIZE=1][suzanna][/SIZE][/FONT]
[FONT=System][SIZE=1]    path = /home/suzanna[/SIZE][/FONT]
[FONT=System][SIZE=1]    read only = No[/SIZE][/FONT]

[FONT=System][SIZE=1][Desktop][/SIZE][/FONT]
[FONT=System][SIZE=1]    path = /home/suzanna/Desktop[/SIZE][/FONT]
[FONT=System][SIZE=1]    read only = No[/SIZE][/FONT]

[FONT=System][SIZE=1][Pictures][/SIZE][/FONT]
[FONT=System][SIZE=1]    path = /home/suzanna/Pictures[/SIZE][/FONT]
[FONT=System][SIZE=1]    read only = No[/SIZE][/FONT]

[FONT=System][SIZE=1][File System][/SIZE][/FONT]
[FONT=System][SIZE=1]    path = /[/SIZE][/FONT]

[FONT=System][SIZE=1][share][/SIZE][/FONT]
[FONT=System][SIZE=1]    comment = Ubuntu File Server Share[/SIZE][/FONT]
[FONT=System][SIZE=1]    path = /srv/samba/share[/SIZE][/FONT]
[FONT=System][SIZE=1]    read only = No[/SIZE][/FONT]
[FONT=System][SIZE=1]    create mask = 0755[/SIZE][/FONT]

[FONT=System][SIZE=1][tmp][/SIZE][/FONT]
[FONT=System][SIZE=1]    comment = temporary files[/SIZE][/FONT]
[FONT=System][SIZE=1]    path = /tmp[/SIZE][/FONT]
[/INDENT]The tmp share is from the testing process.  

As far as users/machines. My primary ID suzanna is User 1000 on the 2 machines I'm working with.  The system identifies both as 'suzanna'  My primary windows ID is Suzanna with the capital.  Admin is SMCrossman (although that was on ly created a couple of months ago..  To avoid confusoin when coping files back and forth in Windows I changed the dell user id to Zan.  Some places it displays as Zan some as Suzanna. Basically I can use either in path name and get the same place.

So how do I add a second suzanna with a different location to the user file?  

thanks for the help folks!

---

### Post by Morbius1 on 2011-06-07
Well, I have to admit I don't know what you're talking about.

* You have as a global parameter "guest ok = Yes" which will dictate who has access ( everyone ) to your shares unless you override that parameter in the share definition sections themselves. According to testparm you have not so all your shares appear to allow guest access.

[COLOR=Blue]EDIT: Sorry forgot this:[/COLOR]

* You have a number of errors here:
> [SIZE=1][FONT=System]Global parameter username map found in service section!
Global parameter guest account found in service section!
lp_bool(root, admin, suzanna): value is not boolean![/FONT][/SIZE]
The "service section" errors means you are using a global parameter within a share definition section and testparm apparently is throwing them away. Not sure about the boolean error.

Side Notes:

(1) There's no law that you cannot create shares within shares but eventually it will get away from you from a management perspective:
> path = /home/suzanna
path = /home/suzanna/Desktop
path = /home/suzanna/Pictures
(2) I wouldn't do this on a drunken bet:
> [FONT=System][SIZE=1][File System][/SIZE][/FONT]
[FONT=System][SIZE=1]    path = /[/SIZE][/FONT]
My best guess is that this isn't a Samba authentication problem but a Linux permissions problem. In order for anyone ( especially guest ) to access the the following share for example ( remember you have a global "guest ok = yes" in place) :
> [FONT=System][SIZE=1][Pictures][/SIZE][/FONT]
[FONT=System][SIZE=1]    path = /home/suzanna/Pictures[/SIZE][/FONT]
[FONT=System][SIZE=1]    read only = No[/SIZE][/FONT]You are going to have to make sure that the directory ( Pictures ) has full rwxrwxrwx permissions and the the parents ( /home/suzanna & /home ) have at least rwxr-xr-x permissions.

---

### Post by smcrossman on 2011-06-07
Thanks!  The errors....the boolean thing I altered the valid users on that line....and obviously I have an issue with how I did it. That I will just work on until I get it cleaned up....although I suppose my smb.conf.orig may tell me what the line was originally.

As far as parent/child folder shares.....I hadn't realized that each one doesn't need to be made into a share.  My system has been a nightmare from day one in Windows and sometimes even with full privileges for directory and folder it won't let me write/alter an individual file.. So since I'm used to that kind of nightmare I just started sharing everything I thought I might need.

As for root....you have a good point. Since I am the only one using any of these computers at the moment I was just thinking about ease of access.  But the netbook is always a point of vulnerability with it being toted around from place to place and all.  Then of course all 3 are accessible (if anyone would care to bother) via DSL I expect despite the DSL firewall and on the windows side the McAfee/Windows firewall. This is where setting up a group and setting valid user (which I spent yesteday exploring) would be better used right?

So that leaves me with the question of how to set up myself as a user 3 times (1 for each machine) and add in another user on windows (netbook).  Since I used the suggested nobody for the gateway windows, do I copy and then edit that for the netbook and then put those users into a group of their own for permissions?  Is there a relatively current documentation on groups & users protocols and setup?

Oh...one more quick question. I am assuming that my more secure option is to use the blasted gateway for my server rather than my netbook.  That way if someone else gets my netbook they don't have my actual server (even if it is just a little home network).

---

### Post by Morbius1 on 2011-06-07
> So that leaves me with the question of how to set up myself as a user 3  times (1 for each machine) and add in another user on windows (netbook).   Since I used the suggested nobody for the gateway windows, do I copy  and then edit that for the netbook and then put those users into a group  of their own for permissions?  Is there a relatively current  documentation on groups & users protocols and setup?
That's the part I don't understand. All your shares allow guest access so there's no need to set up any users. You may have to make an adjustment to the share definition so that anything added by the remote guest can actually be used the the owner of the server. Or of this is a true server in which I mead that it's just serving files to others on the lan and doesn't have a local user ( other than root ) then you can leave it like it is.[FONT=System][SIZE=1]

I must be missing something in the description of your network.
[/SIZE][/FONT]

---

### Post by smcrossman on 2011-06-07
Nah...you're not missing anything.  Basically this could/should be as simple as 3 computers hooked into a network sharing internet access through a wireless router/gateway. Wouldn't that be nice? My life just isn't that simple. After beating my head against the wall for close to 18 months in Windows to do that with just the 2 computers and upgrading Windows on both machines so they will see and communicate, I added the 3rd one back in which is not capable of running windows.  Because my "primary" is the devil possessed gateway I couldn't then do anykiind of sharing or accessing back and forth with it. AND the gateway only reads DVD/CDs and USB drives when and if it feels like it.

So I installed Ubuntu on the gateway. But THEN it would no longer allow the dell access to anything windows or linux  and I again had no existing network. In the meantime after the second install (on the gateway) Samba suddenly appeared on the old computer. I started reading up. Decided to try setting up a 3 way network in Ubuntu. Decided to take the time and really LEARN about HOW to set up a network and security while I was at it.

So what should be really simple and straightforward is complicated by a monster machine. And as each issue comes up I'm looking for the simple easist solution for right now but looking at it as an opportunity to explore and really learn something new.  In the process I am making it all much more complicated than it is.

Todays "networking" task is to check on my sharing privileges on the 3 machines (directories/files, etc) in the home folders. Removing anything un-necessary (since I am understanding that if the Home folder (directory) is open share to everyone, everything inside is open-share UNLESS specified otherwise in folder permissions) Then testing that to see if each pc/user (me) can access things from each computer.  I'm not going to play with user ids or passwords if I can help it.  That is something I still want to learn and play with, but goal 1 is to be able to access documents, etc. from the other machines.

Probably more information than you ever wanted or needed....but just to help clarify.  Thank you for you help! I'll see what cleaning up folder/file permissions does to the tree error I'm getting!

---

