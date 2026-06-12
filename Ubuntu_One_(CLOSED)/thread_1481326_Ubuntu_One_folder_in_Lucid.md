---
title: "Ubuntu One folder in Lucid?"
date: 2010-05-12
forum: Ubuntu One (CLOSED)
---

### Post by freesitebuilder on 2010-05-12
Like many others, my Ubuntu One isn't syncing. But reading the various threads, I'm confused as to whether I should have an Ubuntu One folder as in 9.10?

I did a clean install of 10.04, and assumed that the feature allowing items to be synced from anywhere on my hdd had been implemented and meant that I didn't need a specific Ubuntu One folder. Is that correct?

TIA

---

### Post by joshuahoover on 2010-05-12
> **freesitebuilder said:**
> Like many others, my Ubuntu One isn't syncing. But reading the various threads, I'm confused as to whether I should have an Ubuntu One folder as in 9.10?

I did a clean install of 10.04, and assumed that the feature allowing items to be synced from anywhere on my hdd had been implemented and meant that I didn't need a specific Ubuntu One folder. Is that correct?

TIA

You will still have an ~/Ubuntu One folder, even though you can select to sync other folders within your home folder. 

Were you able to complete the installation steps here? [https://one.ubuntu.com/support/installation/](https://one.ubuntu.com/support/installation/) If so, please try running the following from a terminal session (Applications->Accessories->Terminal): u1sdtool -c; u1sdtool -s;

You should be able to then test if files are syncing by dropping some files in ~/Ubuntu One and see if they update (file emblems change) and show up on the web site at: [https://one.ubuntu.com/files](https://one.ubuntu.com/files)

Thank you,

Joshua

---

### Post by freesitebuilder on 2010-05-13
I had set it up when I installed, and it seemed to work OK at first. Now clicking "connect" does nothing.
u1sdtool gives:
State: LOCAL_RESCAN
    connection: With User With Network
    description: doing local rescan
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE

---

### Post by joshuahoover on 2010-05-13
> **freesitebuilder said:**
> I had set it up when I installed, and it seemed to work OK at first. Now clicking "connect" does nothing.
u1sdtool gives:
State: LOCAL_RESCAN
    connection: With User With Network
    description: doing local rescan
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE

OK, based on that output, you're definitely not connected to the service. And this is after running "u1sdtool -c" in the terminal? Also, are you using Network Manager to connect to the network or something like a usb modem or other hardware/software?

Thank you,

Joshua

---

### Post by freesitebuilder on 2010-05-18
Sorry for the delay in replying. I have a cable modem, through a (in my case) wired router.

---

### Post by joshuahoover on 2010-05-18
> **freesitebuilder said:**
> Sorry for the delay in replying. I have a cable modem, through a (in my case) wired router.

Alright. Can you try the following and let me know the results?

1. In a terminal session (Applications->Accessories->Terminal) run:
```
wget -q [http://launchpadlibrarian.net/34282008/nm-checker](http://launchpadlibrarian.net/34282008/nm-checker)  && python nm-checker
```

Please let me know what the command above outputs.

Then I'll need you to file a bug report following these steps:

1. In a terminal session (Applications->Accessories->Terminal) run:
```
u1sdtool -d; u1sdtool -q; sudo sed -i 's/LOG_LEVEL = logging.INFO/LOG_LEVEL = logging.DEBUG/' /usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/logger.py; u1sdtool --start; u1sdtool -c;
```


2. Then file a bug report at: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)


3. Run the following in a terminal session: run the following command (replacing ###### with the bug number from step 2): apport-collect -p ubuntuone-client ######


4. Attach ~/.cache/ubuntuone/log/oauth-login.log to the bug report


Thank you,


Joshua

---

### Post by freesitebuilder on 2010-05-19
> **joshuahoover said:**
> Alright. Can you try the following and let me know the results?

1. In a terminal session (Applications->Accessories->Terminal) run:
```
wget -q [http://launchpadlibrarian.net/34282008/nm-checker](http://launchpadlibrarian.net/34282008/nm-checker)  && python nm-checker
```

Please let me know what the command above outputs.

Got state: 3

---

### Post by joshuahoover on 2010-05-19
> **freesitebuilder said:**
> Got state: 3

OK, you're connected according to Network Manager. Were you able to file a bug report following the steps I provided? If so, can you post the number here so I can make sure it gets looked into right away?

Thank you,

Joshua

---

### Post by freesitebuilder on 2010-05-20
[https://bugs.launchpad.net/ubuntuone-client/+bug/582710](https://bugs.launchpad.net/ubuntuone-client/+bug/582710)

Now if I click on "connect" it shows my machine and "connect" button remains greyed out, but doesn't sync.

---

### Post by omegaFil on 2010-12-30
I'm sorry about replying in an old thread but I've had the same problem and **solved**. 
I hope this will help: the problem was my old ~/.local/share/ubuntuone; so I did

```

u1sdtool --quit
mv ~/.local/share/ubuntuone ~/.local/share/ubuntuone2
u1sdtool --start

```

(ubuntuone2 was for having a backup, but maybe is useless now) then state changed:

```
u1sdtool --status
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING_ON_BOTH
```

Hope this will work for you.

---

### Post by candtalan on 2011-01-06
> **omegaFil said:**
> I'm sorry about replying in an old thread but I've had the same problem and **solved**. 
I hope this will help: the problem was my old ~/.local/share/ubuntuone; so I did

```

u1sdtool --quit
mv ~/.local/share/ubuntuone ~/.local/share/ubuntuone2
u1sdtool --start

```


Do not be sorry! this code *worked* for my 10.04 system, thanks! My U1 is now saying it is syncing. :-)

My 10.04 was not showing connected and the connect button was greyed out. For the record, this is what I just tried, and found, on my machine fwiw 
```

candt@user1:~$ u1sdtool -c; u1sdtool -s;
State: ROOT_MISMATCH
    connection: With User With Network
    description: local and server roots are different
    is_connected: False
    is_error: True
    is_online: False
    queues: WORKING_ON_BOTH

```

---

### Post by freesitebuilder on 2011-01-06
That's cured it for me too - but now I'm used to Dropbox I probably won't use it, except maybe as backup for my email contacts. And even there it's not ideal, as it seems to back them up alphabetically regardless of address book.

---

### Post by omegaFil on 2011-01-06
:) Very happy to hear it worked for you also.

@freesitebuilder:
Can you please mark thread as [SOLVED]? Thanks

---

