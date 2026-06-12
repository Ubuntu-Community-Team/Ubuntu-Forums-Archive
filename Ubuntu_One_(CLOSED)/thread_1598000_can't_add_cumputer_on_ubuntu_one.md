---
title: "can't add cumputer on ubuntu one"
date: 2010-10-16
forum: Ubuntu One (CLOSED)
---

### Post by Amy_1990 on 2010-10-16
Hi,

I can't add my computer to ubuntu one's web page.I did there website said to do but it was no go
any help

---

### Post by Amy_1990 on 2010-10-18
After days of trying to add my computer to ubuntu one's website i do not think it's going to work and i can't spend any more time trying to get to work because everything is a dead end for me so maybe dropbox will work.I don't know.

---

### Post by dabomb1022 on 2010-10-18
Try this [http://tecn.me/hR6H](http://tecn.me/hR6H)

---

### Post by Amy_1990 on 2010-10-25
Ok i found out why ubuntu one would not show a add computer button and fixed that the network manager had to be shut down i was using a dial up modem at the time so anyone having this kind of problem on ubuntu 10.04 just shut that down with this command in the terminal
> sudo service network-manager stopand try it again.

Now on to my next problem ubuntu one doesn't connect automatically and i have it checked in the start up list and it doesn't sync.

could anyone help me with these problems.
Thanks

---

### Post by Amy_1990 on 2010-10-29
worked out the sync ubuntu one works great one thing that isn't a big deal but does ubuntu one connect automatically because mine doesn't i have to hit the connect at boot

---

### Post by NHclimber on 2010-10-29
Not sure this will help, but I had to completely purge and reinstall U1 to get it to behave. FAQ here [[https://answers.edge.launchpad.net/ubuntuone-client/+faq/778](https://answers.edge.launchpad.net/ubuntuone-client/+faq/778)].

Post back if that doesn't do the trick.

---

### Post by Cerebrux on 2010-11-11
The process for adding your computer is available at the [Ubuntu One setup page]("https://wiki.ubuntu.com/UbuntuOne/Tutorials/Setup").

The instructions below provide workarounds to try in case you run into problems with the steps linked to above.

10.10 (Maverick)

Make sure you have all the latest updates on your computer. Open System->Administration->Update Manager, click the "Check" button, and if there are updates to install, click the "Install Updates" button. Once all the updates are installed, follow these steps:

Open System->Preferences->Passwords and Encryption Keys

Under "Passwords", right-click on Ubuntu One and select Delete

Open Applications->Accessories->Terminal and run:

    >  killall ubuntu-sso-login
     u1sdtool -q; u1sdtool -c 
That command should cause the Ubuntu One SSO dialog to appear. From there you can either sign up for a new Ubuntu One account or add your computer to an existing Ubuntu One account.

10.04 LTS (Lucid)

Some users have reported problems with finding the "Add Your Computer" button in this process. We believe this is due to the Ubuntu One Preferences application (step 1) not launching your default web browser (quickly enough... or at all) in order to proceed to step 2. If performing step 1 does not open your web browser (or a new tab if you already have a browser open) within a few seconds, please

Close the Ubuntu One Preferences application window (if it's already open)
Open your Terminal (located in Applications >> Accessories) and type the following:

> u1sdtool -q; killall ubuntuone-login; u1sdtool -c 
This should force a web browser to open and put you at step 2 of the process. This is a temporary measure so users can get up and running quickly.

If the steps above do not solve the problem for you, it's possible your network connection is managed by something other than Network Manager (USB modem, WICD, etc.) and Network Manager is still installed and running on your computer. If this is the case, Network Manager will either need to be removed or [disabled]("https://help.ubuntu.com/community/NetworkManager#Disabling%20NetworkManager"). The reason for this is because Ubuntu One first checks with Network Manager to see if there is a connection. If Network Manager is running but doesn't have a connection it tells Ubuntu One that and Ubuntu One waits for a connection to be made before moving forward.

[source]("https://wiki.ubuntu.com/UbuntuOne/FAQ/HowDoIAddMyComputer")

---

### Post by Sven6210 on 2010-11-12
I suggest you delete your computer from the UbuntuOne account, then delete the key ring for ubuntuOne in the password manager and you reconnect the computer from scratch to the UbuntuOne account.

I also had problem with the synchronisation once and after I finished the three steps mentioned above it worked well. So maybe you also want to give it a try?

---

### Post by Amy_1990 on 2010-11-12
Thank you,

at the time i was using a dial up modem and the network manager was stopping ubuntu one from letting me add my computer.I have dsl now and it works great well just one problem but i posted that in a thread of it's own.

---

### Post by Bnonn on 2010-11-14
> Open System->Preferences->Passwords and Encryption Keys

Under "Passwords", right-click on Ubuntu One and select Delete
What happens if Ubuntu One isn't listed in here?

---

### Post by andrea000 on 2010-11-14
> **Bnonn said:**
> What happens if Ubuntu One isn't listed in here?

if your running 10.04 and there is no token under passwords and encryption keys then when you click manage account from the preferences it should take you to ubuntu one's website where you can add your pc.

---

