---
title: "Ubuntu One not syncing between two computers"
date: 2010-05-06
forum: Ubuntu One (CLOSED)
---

### Post by megamaced on 2010-05-06
Hi,

I am running Ubuntu 10.04 on two computers. I have set up my Netbook to sync my Pictures and Documents folders. This works perfectly. All my files are uploaded to the Ubuntu One servers and Nautilus shows tick marks for the files and folders which have been synced.. BUT...

I added a second computer to my Ubuntu One account, my main laptop. I right-clicked the same folders (Pictures, Documents) and set to sync. Nothing happened. Nautilus does not show tick marks. New files I create on my laptop are not being uploaded to the Ubuntu One servers. However my Netbook continues to work fine!

On my laptop, if I run u1sdtool -s I get:

connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

And if I run u1sdtool --list-folders I get a return saying my Documents and Pictures are selected!! So why aren't they syncing with my Netbook and Online??

Cheers

---

### Post by joshuahoover on 2010-05-06
> **megamaced said:**
> Hi,

I am running Ubuntu 10.04 on two computers. I have set up my Netbook to sync my Pictures and Documents folders. This works perfectly. All my files are uploaded to the Ubuntu One servers and Nautilus shows tick marks for the files and folders which have been synced.. BUT...

I added a second computer to my Ubuntu One account, my main laptop. I right-clicked the same folders (Pictures, Documents) and set to sync. Nothing happened. Nautilus does not show tick marks. New files I create on my laptop are not being uploaded to the Ubuntu One servers. However my Netbook continues to work fine!

On my laptop, if I run u1sdtool -s I get:

connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE

And if I run u1sdtool --list-folders I get a return saying my Documents and Pictures are selected!! So why aren't they syncing with my Netbook and Online??

Cheers

I'm not sure why this isn't working for you. You shouldn't have to select "Synchronize on Ubuntu One" for the Documents and Pictures folders on your laptop since you already did this on your netbook. Can you file a bug following these steps so I can get a look at the log files from your laptop?

   1.  [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)  - Be sure to include the steps you're taking and the results you're seeing
   2. At a terminal session (Applications->Accessories->Terminal) run the following command (replacing ###### with the bug number from step 1): apport-collect -p ubuntuone-client ######
   3. Attach all ~/.cache/ubuntuone/log/syncdaemon.log files

Thank you,

Joshua

---

### Post by megamaced on 2010-05-07
Hi thanks for responding,

Sorry in this instance I just wanted to get things fixed ASAP so I...

Launched Ubuntu One prefs on the laptop and deleted the account. Then I killed all Ubuntu one processes from the System monitor.

On the netbook I ran u1sdtool --unsubscribe-folder and deleted the Pictures and Documents. Then I deleted the netbook account

With no computer accounts assigned to my account, I ran u1sdtool --start on the laptop, and then opened Ubuntu one prefs which launched Firefox and asked me to add the account, which I did. I then ran the u1sdtool --list-folders which listed my Pictures and Documents folders but not as subscribed. I then ran u1sdtool --subscribe-folder and entered the two ssids for the Pictures and Documents. My laptop got to work immediately syncing those and I can see the tick marks in Nautilus. I repeated exactly the same process on my netbook with the same results.

...So its working now!

---

### Post by joshuahoover on 2010-05-07
> **megamaced said:**
> Hi thanks for responding,

Sorry in this instance I just wanted to get things fixed ASAP so I...

Launched Ubuntu One prefs on the laptop and deleted the account. Then I killed all Ubuntu one processes from the System monitor.

On the netbook I ran u1sdtool --unsubscribe-folder and deleted the Pictures and Documents. Then I deleted the netbook account

With no computer accounts assigned to my account, I ran u1sdtool --start on the laptop, and then opened Ubuntu one prefs which launched Firefox and asked me to add the account, which I did. I then ran the u1sdtool --list-folders which listed my Pictures and Documents folders but not as subscribed. I then ran u1sdtool --subscribe-folder and entered the two ssids for the Pictures and Documents. My laptop got to work immediately syncing those and I can see the tick marks in Nautilus. I repeated exactly the same process on my netbook with the same results.

...So its working now!

Good to hear! If you run into problems getting files to sync, please file a bug like I described above so we can look at some log files and get to the bottom of the problem.

Thank you,

Joshua

---

