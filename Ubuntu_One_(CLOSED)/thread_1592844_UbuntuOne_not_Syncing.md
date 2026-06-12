---
title: "UbuntuOne not Syncing"
date: 2010-10-11
forum: Ubuntu One (CLOSED)
---

### Post by poordamnedfool on 2010-10-11
I was able to get it to start an initial sync.  I had to restart my computer and now all the green checks from my synced folder have disappeared and I cannot sync anything else.

---

### Post by poordamnedfool on 2010-10-11
Running Ubuntu 10.04 32bit PAE kernel.

---

### Post by dabomb1022 on 2010-10-11
Try opening ubuntu one  under System > preferences let me know what happens. I think it might just be turned off

---

### Post by poordamnedfool on 2010-10-11
Did that, it shows my two devices that i have in my cloud but my computer connect button is grayed out and it says im not connected.

---

### Post by duanedesign on 2010-10-11
can you please run the following command in a Terminal and post the results.


```
u1sdtool -s
```

thank you,
duanedesign

---

### Post by poordamnedfool on 2010-10-11
```

    State: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: IDLE

```

---

### Post by tabasko on 2010-10-11
> **duanedesign said:**
> can you please run the following command in a Terminal and post the results.


```
u1sdtool -s
```

thank you,
duanedesign

Hi, Im having troubles too with ubuntu one syncing, bought this morning 20-pack for my photos and clicked them to sync.
But nothing has been synced.

ulsdtool -s gives me


```

State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING_ON_CONTENT

```

---

### Post by poordamnedfool on 2010-10-11
I removed my computer from my cloud and removed the UbuntuOne token then added everything back again and this time it decided to work.  Thanks for the help.

---

### Post by duanedesign on 2010-10-12
> **poordamnedfool said:**
> ```

    State: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: IDLE

```

OK, could you please try the following and let us know if this fixes your issue.

   1. Quit the Ubuntu One Preferences (if open)
   2. Open a Terminal and run this command:
```
    u1sdtool -q; killall ubuntu-sso-login
```
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords" to expand the folder.
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open Me Menu->Ubuntu One or System --> Preferences --> Ubuntu One
   9. a web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer

You now should be able to connect to your account. Let us know how it goes.

EDIT: @poordamnedfool looks like you already figured it out :) I will leave the post for anyone else who is getting AUTH_FAILED when checking the status with 'u1sdtool -s'

thank you,
duanedesign

---

### Post by duanedesign on 2010-10-12
> **tabasko said:**
> Hi, Im having troubles too with ubuntu one syncing, bought this morning 20-pack for my photos and clicked them to sync.
But nothing has been synced.

ulsdtool -s gives me


```

State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING_ON_CONTENT

```

tabasko,
Could you please open a Terminal and run the command:

```
u1sdtool -q; u1sdtool -c
```

Wait about 15 seconds then run u1sdtool -s again and post the result if it is different from the previous result.

thank you,
duanedesign

---

### Post by tabasko on 2010-10-12
> **duanedesign said:**
> tabasko,
Could you please open a Terminal and run the command:

```
u1sdtool -q; u1sdtool -c
```

Wait about 15 seconds then run u1sdtool -s again and post the result if it is different from the previous result.

thank you,
duanedesign

```

State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_CONTENT

```

Thank you, I think now something is happening because my upload is something like 40-80kb/s and I dont have torrent or other network activity going. Maybe now U1 is syncing my files to cloud. I hope this would be permanent solution for this, but at least now I know how to get it woking again. Restarting, or clicking "connect" or "restart" buttons on U1 config did nothing for me.

But still, thanks duanedesign :guitar:

---

### Post by PCTinker on 2010-10-15
I've tried the tips given above repeatedly and I still can't get it to sync. Does the info below help anyone to understand where I'm going wrong?


andy@ubuntu:~$ u1sdtool -s
State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH

andy@ubuntu:~$ u1sdtool -s
State: AUTHENTICATE
    connection: With User With Network
    description: doing auth dance
    is_connected: True
    is_error: False
    is_online: False
    queues: WORKING_ON_BOTH

andy@ubuntu:~$ u1sdtool -s
State: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: WORKING_ON_BOTH

---

### Post by PCTinker on 2010-10-16
I've given up on U1 and opened a DropBox account. It worked, straight out of the box, so to speak, and my DropBox folder syncs with a netbook running xp.
Sorry guys, U1 was just too hard.

---

### Post by poordamnedfool on 2010-10-20
I am still having problems with it syncing.  Is there supposed to be green check marks on the folders that are synced?  U1 says that my folder is synced but in reality it is not, I have more up to date files on my computer than I do in my cloud.  here is a result from u1sdtool -s:

```

    State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

```

---

### Post by Carl Hamlin on 2010-10-22
I'm also having this exact problem, under 10.10. I've tried the suggestions listed here, with strange results.

First, ulsdtool reports:

```

No command 'ulsdtool' found, did you mean:
 Command 'u1sdtool' from package 'ubuntuone-client' (main)
ulsdtool: command not found

```

However, apt-get-install ubuntuone-client reports:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntuone-client is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I've smoked this machine from my account via Ubuntu One preferences, as well as the website, I've deleted the Ubuntu One passphrase from my Passwords and Encryption Keys, etc, etc... Files still don't sync, I still don't get the green checkmark, and the 'Connect' button next to the machine info in Preferences is still greyed out.

Anybody know what gives?

---

### Post by gmendoza on 2010-10-22
> **Carl Hamlin said:**
> I'm also having this exact problem, under 10.10. I've tried the suggestions listed here, with strange results.

First, ulsdtool reports:

```

No command 'ulsdtool' found, did you mean:
 Command 'u1sdtool' from package 'ubuntuone-client' (main)
ulsdtool: command not found

```

...

Anybody know what gives?

The second letter in the command u1sdtool is the number 1... not lower case L.

---

### Post by Carl Hamlin on 2010-10-23
> **gmendoza said:**
> The second letter in the command u1sdtool is the number 1... not lower case L.

Ah. Thanks, gmendoza.

Now I've completed the entire set of troubleshooting steps as described, and am still in the same boat.

Any other ideas? Thanks again for your help; I'd like to see this work.

---

### Post by Dr.Dran on 2010-10-25
Hi!

I've installed Ubuntu 10.10 64Bit and UbuntuOne sync my Tomboy notes, my folder but not my Evolution Contact, Firefox Bookmarks and Chat history :S

Thi is the console output:
u1sdtool -s

```
State: QUEUE_MANAGER
connection: With User With Network
description: processing queues
is_connected: True
is_error: False
is_online: True
queues: IDLE
```

I've in mind to buy the new phone contact service, but if the syncronization of the contact with evolution doesn't do anything I buy a google account :P

Best Regards

Franco

---

### Post by uniomni on 2011-02-27
I have the same problem and have tried the suggested procedure over and over. The process seems fine, no errors are reported and the machine appears on [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/) after connecting.
However, u1sdtool -s still reports
State: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: WORKING_ON_BOTH

Where are the log files where one can troubleshoot this further?

I am running Ubuntu One successfully on several machines but the one in trouble is a Lucid 32 bit desktop that was upgraded from Karmic.

Can you please help?
Thanks
Ole Nielsen 



> **duanedesign said:**
> OK, could you please try the following and let us know if this fixes your issue.

   1. Quit the Ubuntu One Preferences (if open)
   2. Open a Terminal and run this command:
```
    u1sdtool -q; killall ubuntu-sso-login
```   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords" to expand the folder.
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open Me Menu->Ubuntu One or System --> Preferences --> Ubuntu One
   9. a web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer

You now should be able to connect to your account. Let us know how it goes.

EDIT: @poordamnedfool looks like you already figured it out :) I will leave the post for anyone else who is getting AUTH_FAILED when checking the status with 'u1sdtool -s'

thank you,
duanedesign

---

### Post by Gerroo on 2011-03-06
Same problem here with 10.10 Maverick, 2.6.35-27-generic
Followed all steps suggested here several times and one link un- and reinstalling Ubuntu One. Same result.

$ u1sdtool --statusState: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: WORKING_ON_BOTH

syncdeamon.log
ubuntuone.SyncDaemon.Main - NOTE - ---- MARK (state: <State: 'AUTH_FAILED'  (queues WORKING_ON_BOTH  connection 'With User With Network')>; queues: metadata: 1; content: 1; hash: 0, fsm-cache: hit=116 miss=3) ----

In Ubuntu One Preferences Name, Email and Current Plan stay :Unknown
I am not familiar with bug reporting and there seem to be several with the same issue already posted. Could not find any solution after several hours search. I am stuck now.
Any suggestions?

---

### Post by uliba on 2011-04-07
Had the same problem. I noticed that my clock was 5-7 minutes out of sync and I fixed it by syncing the date-time. You can do it either manually (system->admin->time & date) or issuing  on terminal the command:
```
sudo ntpdate-debian
```

---

