---
title: "How about some ideas for securing laptops"
date: 2021-03-19
forum: Security
---

### Post by cyberhiker001 on 2021-03-19
I left my Ubuntu laptop vulnerable and it was stolen. I doubt that the thief was able to unlock the splash password, but he could access with a startup USB.

I was wondering if I could set up a dual boot that would go to an "inert" system, if not prompted at a quick Grub menu, with no password that would open a browser that would then send a location to my email. Any ideas how to do that?

How about also taking a picture of the person who turns it on and sending it to my email, as well?


Also, on my new laptop, I went to the Dconf editor and I came across the login banner, and I added a message offering a reward for return with my email, but it does not show. ???
I tried to do it manually, as well - did not work.???

---

### Post by TheFu on 2021-03-19
No need for any browser.

Setup an MTA like postfix, then at every reboot +2 minutes, have it try to send the current IP address to an email address you control. You could snap a photo from the webcam too, uuencode that and email it out.  While you are at it, why not setup an reverse-ssh connection to a server you control, then you could be really nasty to the other person, until they wipe the OS.

This really won't be very effective, I'm sorry to say. Only a total noob would boot the existing OS.

For the other questions, maybe if you said which release and DE was being run, someone could help?  Also, which instructions did you follow from *.ubuntu.com sites?  Following random instructions on the web that were posted 5+ yrs ago seldom work for point-n-click stuff.

---

### Post by lordgallen on 2021-03-21
This won't help you get your laptop back, but it will make it hard for any thief to use it. Besides encrypting your data with LUKS, you should set a user and admin password in your bios.

---

### Post by ipv2 on 2021-04-20
in the bios of some motherboards there is a feature that allows you to lock your hard disk as well which helps in safe-guarding your data even more.

---

### Post by Skaperen on 2021-04-22
i think he wants to make it easy for a noob to boot up and maybe use because i want to do something like that.

1.  a 2nd hard drive or 2nd partition that is encrypted is the start.

2.  make it look like Windows enough to fool a noob.

3.  make it easy for a noob to configure it to connect to a network service.

4.  make it easy for a noob to run a familiar browser.

5.  do the SMTP thing to your server (or cloud instance) via an obscure port number in case noob's ISP blocks port 25.

6.  do not do the webcam thing if your laptop lights a red light when the camera is on (or do it to scare the noob)

my own plan is to encrypt the 3rd drive, maybe both 2nd and 3rd, but leave the 1st clear and configured to run solo.  from there i'll work out some way to bring up the secure system and reload its kernel and use its secure /usr space.

---

