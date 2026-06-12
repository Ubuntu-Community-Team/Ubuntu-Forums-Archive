---
title: "Ubuntu One doesn't show machine name"
date: 2010-08-13
forum: Ubuntu One (CLOSED)
---

### Post by petri on 2010-08-13
As  you can see in the pictures. It doesn't work on english or swedish. It also freezes wen I change to tab Devices for about a minute. On Services tab none of the alternatives is saved after restart. In my other computer also with Lucid Lynx it works.

---

### Post by duanedesign on 2010-08-13
Can you try the following and let us know the results?

   1. Quit the Ubuntu One client
   2. Open Applications->Accessories->Passwords and Encryption Keys
   3. Click on the arrow next to "Passwords"
   4. Right-click on the Ubuntu One token and select "Delete"
   5. Go to [https://one.ubuntu.com/account/machines/](https://one.ubuntu.com/account/machines/)
   6. Click on the checkbox next to your computer
   7. Click the "Remove selected computers" button
   8. Open Me Menu -->Ubuntu One
   9. a web page should open, prompting you to add your computer to your Ubuntu One account
  10. Add your computer 

If you get the bug where you do not see the 'Add This Computer Button' in step 9 [see this wiki page]("https://wiki.ubuntu.com/UbuntuOne/FAQ#How%20do%20I%20add%20my%20computer?").

---

### Post by petri on 2010-08-13
All 10 steps does work for me I can add this computer but the client freezes for about one minute and then responds again but does not show the right computer name only the standard(?) <LOCAL MACHINE>

Always when I start the client and choose tab Devices it freezes for a minute or so and seems like not working with the server. It is not updating the files although it claims so.

---

### Post by petri on 2010-08-16
Maybe I need to reinstall Ubuntu?

---

### Post by duanedesign on 2010-08-17
Even after checking the Services in the services Tab the client does not connect?

Can you run the following in a Terminal and post the results

```
u1sdtool -s 
```

also look at the file ~/.cache/ubuntuone/log/syncdaemon-exceptions.log you can use the command:

```
gedit ~/.cache/ubuntuone/log/syncdaemon-exceptions.log
```

if this has something in it could you post it. Please post all code in the CODE TAGS. It is the # in the message post tools.
-
-

---

### Post by petri on 2010-08-17
No it doesn't connect nor show right computer name.

```
~$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing queues
    is_connected: True
    is_error: False
    is_online: True
    queues: IDLE
```

and the **syncdaemon-exceptions.log** is empty.

---

### Post by petri on 2010-08-25
Nowadays this is non issue for me. My laptop crashed, it shows only blank screen I can't get into the bios and LiveCD doesn't show up either. Thanks anyway.

---

