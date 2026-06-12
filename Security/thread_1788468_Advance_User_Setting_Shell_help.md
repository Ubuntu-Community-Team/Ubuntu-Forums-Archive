---
title: "Advance User Setting Shell help"
date: 2011-06-22
forum: Security
---

### Post by Kulas101 on 2011-06-22
As I was researching on how to create a kiosk Ubuntu setting I came upon a suggestion to create the user with '/usr/bin/screen' shell option. 
Hope you all would forgive me for this noob question but what does this mean? 
I saw when I checked the Advance Settings Advance tab that there are a couple of possible options there, what do they mean and how will they affect the user profile I'm creating? 
I tried google for this and if my understanding is correct, these shells are suppose to be programmable and a scripting language for linux but I'm confused on what effect this has on the user profile I'm creating? 
One thing I notice though is that with the '/usr/bin/screen' option, the user account is refused of the Applications > Accessories > Terminal option.
When I googled each one of the options I'm getting more confused as to the relevance of this to the user profile. :(

If anyone can provide me short descriptions and explanations for its relevance on the user profile, or can point me to a link or page site I should be reading, I'd really appreciate it. 

/bin/bash
/usr/bin/screen
/bin/sh
/bin/dash
/bin/rbash
/bin/false

Thank you very very much. ;)

---

### Post by BkkBonanza on 2011-06-23
The **screen** program allows having multiple consoles open under one login. So you can start some process in one and switch to another and do something else, then switch back easily. There are other handy features too. You can read more with **man screen** (assuming you have installed it).

Using it as a shell (though I'm kindof adlibbing here as I don't do this usually) allows a login session to be attached to by other users. So this would be good when you need someone to help you thru a process - they could attach to your screen and do commands while you watch. Of course, having that setup could also be a security issue as someone could watch your session and do things you may not be aware of.

Having a shell set as /bin/false just indicates that the user cannot login to a shell, ie. no shell allowed. This is useful for users that are setup for internal stuff like running a cron job or as a file owner but one that should not be able to login remotely, which reduces potential for abuse.

The other ones you list look like various alternative shells that are similar in ways to the regular bash shell. Oh and "shell" means the program that will interpret the user commands when you login and execute them or call a program as needed. A shell can be made to limit the abilities of what a user can do. For example, having the sftp shell for ssh allows only doing sftp (secure file transfer) commands, and not running programs.

---

### Post by Kulas101 on 2011-06-23
thank you for the reply Bkk ;)

reading from your reply and after previous weeks of research, i realized that i have much to learn of ubuntu, especially the ins and out of its security customization and how it operates.
i think i need to really study this one and some other aspects of the OS so to be more confident with the kiosk system we're trying to implement.
so far we are having progress, though slowly and much trial and error.
the articles in these forums really helped us a lot, thank you and to the guys who gave their time in answering the queries here in the forum.

for now we are happy though very nervous on our existing implementation, its a work in progress.
happy because it seems to be working, nervous because of our lack of knowledge of ubuntu OS as a whole.

we are crossing our fingers. :KS

---

### Post by i.r.id10t on 2011-06-23
For the kiosk systems I set up, I use the rkiosk firefox extension as well as make the kiosk users home directory not writeable (after doign all of my settings, etc).  Works well.

---

