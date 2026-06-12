---
title: "System 76 User Manuals"
date: 2008-05-25
forum: System76 Support
---

### Post by davahmet on 2008-05-25
I recently received my new Pangolin laptop but thought it rather odd that no user manual shipped with it.  I understood some of the more obvious controls on the laptop, but I'm unsure of others, such as, the buttons labeled "Wow video" and "Wow audio".  What are these for?  Also, I have yet to figure out just how to turn on the web-cam that came with the NVidia card.  I believe that these questions would normally be clarified in a user manual.

Since no manual was shipped, is there one available on-line?

---

### Post by thomasaaron on 2008-05-26
The WoW buttons are unassigned. They could be assigned by you to different things, as they do produce a keycode.

You don't have to do anything to turn on your webcam. It has been tested with Cheese (which can be downloaded from the repositories) and Ekiga Softphone (which is located at Applications > Internet > Ekiga). Customers are also using it in Skype. In short, it is supported by programs that use the V4L2 protocol. Not all programs do, but it is becoming more popular.

Users manuals are typically written to describe the computer functionality running Windows, which often does not coincide with its functionality under Linux. This is why we are so active in our email and forum support. That said, a user's manual is something we've considered. There's a good chance computers may be shipped with them in the future.

---

### Post by VOLKOV9 on 2008-08-19
I can't reply to this related thread (I guess because it's in the ge domain?): [http://ge.ubuntuforums.com/showthread.php?t=786857](http://ge.ubuntuforums.com/showthread.php?t=786857)

Anyway, the list provided by Keytouch does not have any entry that includes "intel," "generic," or "105."  Could you look at the list and pick an entry that should work for the Serval?

Thanks very much.

---

### Post by bboston7 on 2008-08-19
The manual is digital on the computer.  I think it is under help.

---

### Post by Naenyn on 2008-08-20
> **VOLKOV9 said:**
> I can't reply to this related thread (I guess because it's in the ge domain?): [http://ge.ubuntuforums.com/showthread.php?t=786857](http://ge.ubuntuforums.com/showthread.php?t=786857)

Anyway, the list provided by Keytouch does not have any entry that includes "intel," "generic," or "105."  Could you look at the list and pick an entry that should work for the Serval?

Thanks very much.

Not exactly the right spot for this post, but...

VOLKOV9,

I used the Keytouch editor to make my own keyboard file with definitions for the Wow Video and Wow Audio keys.

I've attached the file to this post. Feel free to give it a shot. One note is that this was created for a Serp4. Dunno how it'd work on other s76 laptops.

When Keytouch starts up, select 'import', then the file.. it'll show up as 'Generic' manufacturer, '105-key (Intel)' model. You can always just make your own with the keytouch editor too if you want. =]

-naenyn

---

