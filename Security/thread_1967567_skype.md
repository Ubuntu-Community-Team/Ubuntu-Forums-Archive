---
title: "skype"
date: 2012-04-28
forum: Security
---

### Post by bhoopal on 2012-04-28
hi guys, I'm on Ubuntu 12.04 LTS. the problem is that, since I've been using Skype for Linux, i keep getting dirty message from stranger, though in the privacy settings, i opted to receive calls and chats only from people i have allowed. On windows i was not getting these messages. they even call at times. then i block the user, report abuse, and delete the event. it stops, but soon other strangers starts sending instant messages. I reported the problem to Skype a few days ago, but got no response. i upgraded from 11.10 to 12.04 today, still same problem.
my Skype version is beta 2.2.0.35.
i'm sorry if i posted in the wrong place, i didn't see any post for Skype, not even in the 3rd party. I think they strangers might actually be programs, spams...so i put it in security thread

---

### Post by bhoopal on 2012-04-28
[16:59:32 MUT] kerem_alemdaroglu: hello
[17:01:33 MUT] kerem_alemdaroglu: how are you
[17:13:23 MUT] * USER left the chat (Only people who have accepted contact request can be added).


this is a non dirty example.

---

### Post by Ms. Daisy on 2012-04-28
I would guess that you've got your skype name posted somewhere public. If you don't want people to know your user name, then don't post it on websites. Create another account, this time don't give it to anyone but your friends. See if it happens with that account.

---

### Post by bhoopal on 2012-04-28
no, its not on any website. and when i use the same account on a windows machine, this does not happen. and i'm pretty sure these are software,spams, and not real person. because sometime the message look alike though they are from different names.

---

### Post by bhoopal on 2012-04-28
Hello Yogesh,

 

 

Thank you for contacting Skype Customer Service.

 

We understand your concerns regarding your Skype privacy and the unwanted calls and messages that you are receiving. We apologized for the inconvenience this may have caused. We are glad to assist you on this.

 

The alert message that you received has been sent by a company that is trying to advertise their product, by advising users that their machines have low levels of security. 
 
These messages are not based on any real information from your computer, and therefore are not reliable. Please ignore this chat alert. 
 
If you receive chat messages or calls from people you do not know, you may need to change your Skype privacy settings. You can change your privacy settings in Skype to only allow calls or chats from people in your Contact List. 
 
You can also block and report abusive users, which will help us to identify and prevent spammers. To block someone already on your contact list who is sending you instant messages:

Ctrl+click on them in your contact list and select Block [Skype Name of the person harassing you].
You will then be asked to confirm that you wish to block them. You can also click the Report abuse from this person checkbox and the details of the account will be sent on to Skype.
Click Block to confirm.
Signing out securely from Chats 
In addition, you should ensure that when you leave a chat and you no longer wish to share contact details with the contact, that you type /leave in the chat window. This ensures that you cannot be added back to that same chat.  
 
You can rest assured that we’re working hard behind the scenes to combat spam, and will take action against spammers where appropriate.

 

We hope you found this answer helpful. Should you need any further assistance or have additional questions please do not hesitate to contact us again.

 

 

 

Best Regards,

Erda S.
Skype Customer Service

---

### Post by bhoopal on 2012-04-28
the above is the reply from skype

"The alert message that you received has been sent by a company that is trying to advertise their product, by advising users that their machines have low levels of security."
does ubuntu have low level of security?? can i use some kind of firewall to block it?

---

### Post by Ms. Daisy on 2012-04-28
See the [basic security wiki]("https://wiki.ubuntu.com/BasicSecurity") for getting started securing ubuntu

---

### Post by bhoopal on 2012-04-29
thank you miss Daisy! i went on the site, read, and install the apps. 
i set a firewall using method 2 on this thread
[http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

I stopped getting the spams. i can browse, use skype, check mails, download...
the only thing i can't do is check my gmail on thunderbird. i cant do it on the web with my browser however. i guess i have to enable a port, but i'm not sure about it. can you help me please. thanks :-)

---

### Post by bhoopal on 2012-04-29
result for "sudo ufw status"
Status: active

To                         Action      From
--                         ------      ----
25,53,80,110,443/tcp       ALLOW OUT   Anywhere
53,67,68/udp               ALLOW OUT   Anywhere
51413/tcp                  ALLOW OUT   Anywhere
51413/udp                  ALLOW OUT   Anywhere
6969/tcp                   ALLOW OUT   Anywhere
25,53,80,110,443/tcp       ALLOW OUT   Anywhere (v6)
53,67,68/udp               ALLOW OUT   Anywhere (v6)
51413/tcp                  ALLOW OUT   Anywhere (v6)
51413/udp                  ALLOW OUT   Anywhere (v6)
6969/tcp                   ALLOW OUT   Anywhere (v6)

---

### Post by OpSecShellshock on 2012-04-29
Your preferences for Thunderbird should have a section for connection settings, and that will show the port that is used for incoming/outgoing messages. It's standard, but at the moment I can't remember what it is. You'll want to allow that one out as well, and then it should connect with no problems.

---

### Post by bhoopal on 2012-04-30
ok, i added a bit randomly though, port 465 out, 993 in and out.. its working.

---

### Post by bhoopal on 2012-04-30
thanks guys. I stopped getting the skype spams

---

