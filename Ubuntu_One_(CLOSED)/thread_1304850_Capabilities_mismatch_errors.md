---
title: "Capabilities mismatch errors"
date: 2009-10-29
forum: Ubuntu One (CLOSED)
---

### Post by joshuahoover on 2009-10-29
A few Ubuntu One users have reported a bug ([#462828]("https://bugs.launchpad.net/ubuntuone-client/+bug/462828")) in the desktop client software that could cause files to become unavailable in some circumstances. As a temporary measure, we have updated our server to display a “Capabilities Mismatch” error to prevent files from becoming unavailable to users.


 A client software update will be released very soon in the update channel. Manually running Update Manager will update your client to work with the server and fix the root cause. Throughout this period, all files are still available from the [Ubuntu One website]("http://one.ubuntu.com/files").
 Contact syncing and Tomboy syncing services have not been affected by this issue.


 **UPDATE**: A new client is available now for beta PPA users running 9.04 and 9.10. More updates coming soon.

---

### Post by joshuahoover on 2009-10-29
The updated Ubuntu One client software is now available to those running Ubuntu 9.10 and not using the beta PPA. Please run Update Manager to install the new software.

Thank you,

Joshua

---

### Post by ashgoodman on 2009-10-30
Still not working for me. Brand new installation. Newly updated. Still getting a capabilities mismatch message.

---

### Post by bertmanphx on 2009-10-30
Hello,
Well, I just updated UbuntuOne, and I do not get the mismatch error.  However, I don't see my contacts magically appearing on the web interface either.

bertmanphx

---

### Post by xodis on 2009-10-30
I am getting the error on a brand new and up to date install.

---

### Post by wrgb2 on 2009-10-30
Update manager says my Ubuntu 9.10 and my Xubuntu 9.10 or both up to date, but I am still getting the Capabilities mismatch error on both machines.

Randy

---

### Post by bhart007 on 2009-10-30
Same here :(

---

### Post by Kruptein on 2009-10-30
I've the same problem,
update manager says everything is up to date :(

---

### Post by Merovius on 2009-10-30
I updated this morning and the message is now gone. :)

---

### Post by michillin212 on 2009-10-30
Same thing here just updated a few minutes ago, restarted, nothing....  Help plz

---

### Post by jperez on 2009-10-30
I just updated UbuntuOne and it worked, but the icon in the tray disappeared. :x

Jesse~

---

### Post by RC1139 on 2009-10-30
make sure your software sources include canonical archive

---

### Post by GTP-Hank on 2009-10-30
I had to check "pre-release" in the update tab of Software Sources to see the fixed ubuntuone client package (1.0.2-0ubuntu2) in the update manager.

Then it took a restart to clear the error message.

HTH

I'm sure it will be pushed from pre to regular update soon, if you don't want to bother.

---

### Post by Sennaista on 2009-10-30
I ran the update manager and there was indeed a new update for Ubuntu One. After installing it the error message went away but if I copy a file into Ubuntu One folder a message comes up that it's being uploaded but nothing actually get uploaded and the little cloud in the notification area has an exclamation mark on it. When I right click on it and click on "connect" the exclamation mark disappears for a while and then comes back.

That's it.

---

### Post by ashgoodman on 2009-10-31
Just updated again this morning, still same problem.

In fact the whole process of upgrading to Karmic Koala was a mess. The upgrade failed and left me with a computer that wouldn't boot.

I did a total clean install on a new hard drive after that and have had nothing but trouble.

Regardless of which repositories I enable or where I download updates from I keep getting errors like this:

GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.

This problem began with gutsy (about 1 out 0f 10 update attempts) and has continually worsened to every update attempt now with Karmic. 

Empathy doesn't show all the contacts that are online and loses connections more often than pidgin. I like the potential of empathy, but its not ready yet and shouldn't have been included in Karmic.

Activating restricted drivers for nvidia had to be done twice for it to work. The Hardware Driver manager gave me 3 options for the nvidia driver and aside from marking one as 'preferred' it gave no indication of what was different between them or why the preferred one is preferred. All 3 had identical descriptions and all 3 said "needs to be activated to enjoy advanced desktop effects"

Compared to 9.04 : 9.10 does NOT boot faster to the desktop and is noticeably sluggish when running compiz

Firefox is bleeding memory all over the place, I have to restart firefox every couple of hours when I used to be able to run it for days.

Prism doesn't seem to be working properly. Half the time only one instance of prism will run at a time. It also seems to be starting the wrong prisms, for example when I click the google reader prism, the facebook prism opens instead. (I double checked and yes, the google reader prism points to google reader but nevertheless, its opens to facebook.

Also when creating a prism, your given the choice of using an icon found on the we or one of your own, regardless of your choice: the icon is NOT used! The prism always is the tacky looking text file icon. Your also given a choice of where to place the shortcut for your new prism... but the only choice is the desktop.. so why give the choice?

And as we have been talking about on this thread, I cant seem to attain Oneness with the Ubuntu One due to a mysterious capabilities mismatch...

This is the worst ubuntu release I have ever seen and I have been using ubuntu since 7.04

Can't wait for 10.04!

---

### Post by sandeepjshenoy on 2009-10-31
> **wrgb2 said:**
> Update manager says my Ubuntu 9.10 and my Xubuntu 9.10 or both up to date, but I am still getting the Capabilities mismatch error on both machines.

Randy

Had the same problem initially. I removed the** ubuntuone ppa beta** package and all other ubuntuone packages. Installed ubuntuone again but not the ppa beta package. Everything is working great now. No mismatch errors.

---

### Post by wrgb2 on 2009-10-31
Thanks sandeepjshenoy, I uninstalled and reinstalled Ubuntu One and it's related files - there are 4 of them in Ubuntu, the Ubuntu One Client, two Python Ubunto One entries, and Ubunton Beta PPA - use Synaptic Package Manager and search for Ubuntu One.  In Xubuntu, the four files are 2 Python Ubuntu One entries, the Ubuntu One Client, and the Ubuntu One Client Gnome.  That fixed the problems on both machines.

Randy

---

### Post by ashgoodman on 2009-10-31
Uninstall and reinstall is NOT working for me. Even did a restart in between. Still can't connect to ubuntu one

---

### Post by sandeepjshenoy on 2009-10-31
> **ashgoodman said:**
> Uninstall and reinstall is NOT working for me. Even did a restart in between. Still can't connect to ubuntu one

Did you remove the ppa beta package?

---

### Post by FuturePilot on 2009-10-31
Still not working for me on Jaunty. It still says capabilities mismatch. It seems to be working on Karmic though.

---

### Post by castrojo on 2009-11-01
Your mirror might be out of date if by now you haven't received the update.

---

### Post by jakslev on 2009-11-01
Hi Everybody!

Solution follows:

1) Go to "Update Manager" and choose "Settings"
2) Here you click the first tab "Ubuntu Software"
3) Then choose "Main Server" in the "Download from" drop-down menu. 

Problem is that the update has not been sent out to all servers - e.g. it is not available on my own Spanish server.

Please, also note that they seem to be working hard on the Ubuntu One thingy; as it was offline for me all evening today (from 7PM and forwards); just returning an error 503 on entering one.ubuntu.com. 

jakslev

PS: Having seen my fine post above I just saw that the answer had already been given..

---

### Post by FuturePilot on 2009-11-01
> **whiprush said:**
> Your mirror might be out of date if by now you haven't received the update.

I received an update from the PPA the same day this problem happened, but it's still not working.

---

### Post by Martin_sensei on 2009-11-02
Hello all,

I had a few problems which sound similar to some of your experiences.

Even after running updates, I still got the error.

In the end I opened up Synaptic Package Manager, searched for ubuntu One, then manually set the installed one packages to be fagged for update.  An update then ran, and everything worked.

Hope this helps someone!

Cheers

Martin

---

### Post by lavinog on 2009-11-02
I finally figured out why I kept getting this error.
I had ubuntu-client 1.1 carried over from jaunty.  The latest version for karmic is 1.02.  The update manager was keeping the newer version which was actually older.

Why is the newer version number less than the older number?

apt logs:
```

Setting up python-ubuntuone-client (1.1+r269-0ubuntu1~ppa1~karmic) ...
Setting up ubuntuone-client (1.1+r269-0ubuntu1~ppa1~karmic) ...
Setting up ubuntuone-client-gnome (1.1+r269-0ubuntu1~ppa1~karmic) ...
...

Removing ubuntuone-client-gnome ...
Removing ubuntuone-client ...
Removing python-ubuntuone-client ...
Removing python-ubuntuone-storageprotocol ...
Selecting previously deselected package python-ubuntuone-storageprotocol.
Unpacking python-ubuntuone-storageprotocol (from .../python-ubuntuone-storageprotocol_1.0.0-0ubuntu1_all.deb) ...
Selecting previously deselected package python-ubuntuone-client.
Unpacking python-ubuntuone-client (from .../python-ubuntuone-client_1.0.2-0ubuntu2_all.deb) ...
Selecting previously deselected package ubuntuone-client.
Unpacking ubuntuone-client (from .../ubuntuone-client_1.0.2-0ubuntu2_all.deb) ...
Selecting previously deselected package ubuntuone-client-gnome.
Unpacking ubuntuone-client-gnome (from .../ubuntuone-client-gnome_1.0.2-0ubuntu2_amd64.deb) ...
Setting up python-ubuntuone-storageprotocol (1.0.0-0ubuntu1) ...
Setting up python-ubuntuone-client (1.0.2-0ubuntu2) ...
Setting up ubuntuone-client (1.0.2-0ubuntu2) ...
Setting up ubuntuone-client-gnome (1.0.2-0ubuntu2) ...

```

---

### Post by joewski on 2009-11-02
> **lavinog said:**
> I finally figured out why I kept getting this error.
I had ubuntu-client 1.1 carried over from jaunty.  The latest version for karmic is 1.02.  The update manager was keeping the newer version which was actually older.

Why is the newer version number less than the older number?



I was having the same problem. Thanks for your post.
In case you do not know what to do to fix the problem do the following on the gnome desktop.

0. System -> Software sources
1. select other software
2. delete entries for ubuntuone beta (should be two)
3. System -> Synaptic Package manager
4. Search for ubuntuone
5. Completely remove all application with ubuntu one in the name.
Don't worry about password settings or your files in the ubuntuone directory they don't get lost or deleted.
6. Reboot the machine to kill the running ubuntuone service.
7. System -> Synaptic Package manager
8. Search for ubuntuone
9. check all the ubuntuone related apps
10. apply and close synaptic.
11. next alt-f2 and type in ubuntuone to launch ubuntuone for the first time.
12. Ubuntuone should now automatically start when you login.

---

### Post by lavinog on 2009-11-02
> **joewski said:**
> 
6. Reboot the machine to kill the running ubuntuone service.


you should be able to right click the icon on the status bar and click quit instead.

---

### Post by Aerodynamic on 2009-11-03
I also first did get this message, but now i don't..but if i klick on "connect" in the Ubuntu folder nothing happens..

Client update for Ubuntu One? when? Have all the updates released through update manager, and have tried to activate "pre-released updates" in software sources..

Using Karmic.

---

### Post by joewski on 2009-11-03
> **lavinog said:**
> you should be able to right click the icon on the status bar and click quit instead.

I choose that method because some users don't have the icon displayed if there is no activity on ubuntu one. Also there may be multiple users using the machine so simple closing ubuntu one may not shut it down completely. In any case if your advanced enough it doesn't matter which method you choose to kill ubuntuone so long as it works.

---

### Post by RealG187 on 2009-11-09
What command can I type to update to the latest Ubuntu One?

---

### Post by joewski on 2009-11-10
> **RealG187 said:**
> What command can I type to update to the latest Ubuntu One?

There is no command you need to type. Ubuntu keeps track of what needs to be updated through update manager. You only need to initiate ubuntuone.

---

### Post by RealG187 on 2009-11-10
I prefer to use commands for package management. Like apt-get.

Is there a way I can update it from the terminal?

---

### Post by jaxån on 2009-11-15
Try
[FONT="Courier New"]sudo aptitude update
sudo aptitude upgrade[/FONT]

or

[FONT="Courier New"]sudo apt-get update
sudo  apt-get upgrad[/FONT]e

---

### Post by Aerodynamic on 2009-11-16
I was first having the RC version(Karmic) and did all the distribution upgrades through "update manager" a couple of days ago..same problem..did a reinstall of Karmic(this time not the beta version) yesterday...problem solved =) no errors and the ubuntu client is synchronizing automatically =)

---

### Post by Ba7r on 2010-09-01
[FONT=Tahoma][SIZE=4][COLOR=Blue][B]Try this 

sudo apt-get update

It's useful 


Regards 
[Muhammed]("http://google-yahoo-user.blogspot.com/")
[/B][/COLOR][/SIZE][/FONT]

---

