---
title: "Ubuntu Phone contacts backup"
date: 2015-04-02
forum: Ubuntu Phone and Tablet
---

### Post by chris-burmajster on 2015-04-02
Hello,

I have one of the new Ubuntu phones and one of the major problems I had with it was that, having carefully saved all my contacts onto the SIM card in my previous phone, the Ubuntu phone cannot read them. I bit the bullet and put each contact in by hand - over an hour's work. Having done that and not wanting to have to do it all over again, is there any way I can backup the new contacts list?

I have already connected the phone to my Ubuntu desktop and a number of folders show, but no contacts and I looked inside each and every folder and subfolder and viewed hidden files too. It must live somewhere!

Many thanks,

Chris

---

### Post by Lars_Roth on 2015-04-03
Not an expert so unfortunately no help from me. My contacts were already synced with Google. Downloaded easily without any problem at all.
Are you against having it in the cloud?
Secondly, if you were going t transfer, was it not possible to bluetooth? I have done that with other phones before

---

### Post by ian-weisser on 2015-04-03
On desktop systems, evolution-data-server data, including contacts.db, is within /home/$USER/.local/share/evolution/

Since it's within /home, it should be automatically  included if you backup or migrate your /home to preserve your personal data, your settings, etc.

I lack an Ubuntu Phone, so you will want to verify that contacts.db is in the same location.

---

### Post by chris-burmajster on 2015-04-03
> **Lars_Roth said:**
> Not an expert so unfortunately no help from me. My contacts were already synced with Google. Downloaded easily without any problem at all.
Are you against having it in the cloud?
Secondly, if you were going t transfer, was it not possible to bluetooth? I have done that with other phones before

Yes, I'm a bit of a tin foil hat type, especially after all the Snowden revelations. I don't touch anything Google with a barge pole. I take the point about bluetooth, it's just that I was unable to find where the contacts live. It's a little different to desktop Ubuntu. That's why I now want to back them up.

Chris

---

### Post by jacktar on 2015-04-03
All you need to do is backup your contacts to your email address with MCbackup then mail the contacts to the new phone.

---

### Post by Lars_Roth on 2015-04-04
I cannot see any files besides video, music, documents...
no files shoving os.

---

### Post by ian-weisser on 2015-04-04
.local, like other '.' files, is hidden by default.
On a desktop, you show them using CTRL+h. Not familiar with how to show them on a phone, sorry.

---

### Post by info-velthuizen on 2015-04-04
You only can put something using a ssh connection to your phone, the easiest way is to copy your address book is with a Google Gmail account. I know you don't like it that way but it work as a charm, and you can remove your Google account afterwards. :p

---

### Post by chris-burmajster on 2015-04-15
I found out how to do it, with help from yourselves. I installed FILE MANAGER on the phone from the Ubuntu Store, ran it and enabled 'show hidden files'. Using the broad path in ian-weisser's post, I found the contacts.db file. I then fired up Dekko (the e-mail program on the phone) and sent myself an e-mail attaching the contacts.db file. Now I have the backup!

Thank you to all of you for your help and suggestions.

Chris

---

### Post by Steffen_Englert on 2015-11-22
> **chris-burmajster said:**
> I found out how to do it, with help from yourselves. I installed FILE MANAGER on the phone from the Ubuntu Store, ran it and enabled 'show hidden files'. Using the broad path in ian-weisser's post, I found the contacts.db file. I then fired up Dekko (the e-mail program on the phone) and sent myself an e-mail attaching the contacts.db file. Now I have the backup!

Thank you to all of you for your help and suggestions.

Chris

Hello Chris, 

where did you find the file "contacts.db"? I installed FILE MANAGER, enabled "show hidden files" but can't find my contacts anywhere. Thanks for your help!

Steffen

---

### Post by chris-burmajster on 2015-11-23
Hi Steffen,

You can get it via 
~/.local/share/evolution/

that's in file manager, with root access, and unlocked.

Hope this helps,

Chris

---

