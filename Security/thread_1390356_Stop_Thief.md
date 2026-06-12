---
title: "Stop Thief"
date: 2010-01-25
forum: Security
---

### Post by Roland TD-12 Rat on 2010-01-25
Hi all,
I have a sister who is a ground breaking artist. [www.daphne-dorney.co.uk](www.daphne-dorney.co.uk)
sadly she has been cracked and sabotaged on a number of occasions. I am aware that linux is generally more secure than WINDOWS :-( but, I really don't understand the mechanics. Can someone enlighten me ii lay man's terms?

---

### Post by REDace0 on 2010-01-25
I'm not a security expert, but generally Linux is more secure than windows because it is rarer to give the user Super User or Administrator authority than it is in Windows. Regarding the security of her website, I'm sure the Ubuntu users who run their own web servers will need more info about the hacks so they can figure out why her site is being breached.

---

### Post by Grenage on 2010-01-25
It is, and it isn't (are there ever clear-cut answers).

Linux has a tiny market share compared to Windows, so tools and techniques that are sculpted for the masses don't work on it.  Linux distributions also tend to use more secure methods by default.

In all honestly, user habit make the biggest difference; never install software that you can't trust!  How many people download random executables and install them, just to get some 'hilarious' emotes?

Use different passwords (and possibly user names) on different accounts.  Many people use the same password for their hotmail and 100 other online services, when one is compromised, they all are.

If it's the web server itself that's been compromised, well then that's down to the host to look at (within reason).  Both Apache and IIS can be very secure.

---

### Post by cdenley on 2010-01-25
> **Roland TD-12 Rat said:**
> Hi all,
I have a sister who is a ground breaking artist. [www.daphne-dorney.co.uk](www.daphne-dorney.co.uk)
sadly she has been cracked and sabotaged on a number of occasions. I am aware that linux is generally more secure than WINDOWS :-( but, I really don't understand the mechanics. Can someone enlighten me ii lay man's terms?

The username "thesandman" is revealed in that page, and you are running an FTP server. Does that user have a strong password? Can root login with FTP? Is the root password strong?

I don't recommend FTP without SSL encryption.

---

### Post by doas777 on 2010-01-25
in this case it is the app (the site itself) that appears to be insecure. no idea about the server, but if you put an insecure app on a secure server, all you have managed to do is unsecure the server.

find a webmonkey that doesn't use frontpage would be my first recommendation.

---

### Post by bodhi.zazen on 2010-01-25
> **Roland TD-12 Rat said:**
> Hi all,
I have a sister who is a ground breaking artist. [www.daphne-dorney.co.uk]("http://www.daphne-dorney.co.uk")
sadly she has been cracked and sabotaged on a number of occasions. I am aware that linux is generally more secure than WINDOWS :-( but, I really don't understand the mechanics. Can someone enlighten me ii lay man's terms?

Try these links.

[http://en.wikipedia.org/wiki/Comparison_of_Windows_and_Linux#Security](http://en.wikipedia.org/wiki/Comparison_of_Windows_and_Linux#Security)

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

Also FTP is insecure for a variety of reasons, use an encrypted protocol such as ssh (scp , sftp)

---

### Post by Roland TD-12 Rat on 2010-01-26
> **cdenley said:**
> The username "thesandman" is revealed in that page, and you are running an FTP server. Does that user have a string password? Can root login with FTP? Is the root password strong?

I don't recommend FTP without SSL encryption.
Hi 
Please understand I know very little about all this stuf but:
'thesandman' was the PC user name on an earlier installation of linux,and the pc has since been wiped and reinstalled. 'the sandman ' is not the user name for logging into the ISPs server. FTP is only being used for upload to the host, but I think what you say was very likely relevant before the PC was re-jigged, since I am convinced the break in was via her router (wifii) and not at server level. First get on to the users machine, find out their login details for the host, and bingo you become the user? Am I making any sense?

---

### Post by Roland TD-12 Rat on 2010-01-26
> **doas777 said:**
> in this case it is the app (the site itself) that appears to be insecure. no idea about the server, but if you put an insecure app on a secure server, all you have managed to do is unsecure the server.

find a webmonkey that doesn't use frontpage would be my first recommendation.
I'm pretty confident about the server, but confess to being the fronpage user :-(.
Do you have any recommendations for future use? I'm no good with straight HTML Tempting providence, however, all has been quiet since she has been in New Zealand. I suspect her use of wifii in the UK as having given someone nearby an in on her PC.
Please, no laughter if this is Naive as I am not very knowledgable on this sort of thing.

---

### Post by Roland TD-12 Rat on 2010-01-26
> **bodhi.zazen said:**
> Try these links.

[http://en.wikipedia.org/wiki/Comparison_of_Windows_and_Linux#Security](http://en.wikipedia.org/wiki/Comparison_of_Windows_and_Linux#Security)

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

Also FTP is insecure for a variety of reasons, use an encrypted protocol such as ssh (scp , sftp)
Thanks, Im off to try the links. I'll mark the thread as solved and do some research :-)

---

### Post by doas777 on 2010-01-26
> **Roland TD-12 Rat said:**
> I'm pretty confident about the server, but confess to being the fronpage user :-(.
Do you have any recommendations for future use? I'm no good with straight HTML Tempting providence, however, all has been quiet since she has been in New Zealand. I suspect her use of wifii in the UK as having given someone nearby an in on her PC.
Please, no laughter if this is Naive as I am not very knowledgeable on this sort of thing.

I'm sorry to say, any serious web app (one that sells products or otherwise handles sensitive info) should be done by a professional. there is just too much to get wrong. 

now don't get discouraged; experience is important and you get that by working and experimenting, so by all means work on developing a site. just don't get too ambitious about the feature set just yet. afterall, if your site holds nothing that can hurt you, all you have to worry about from a security perspective, is repairing vandalism, and protecting your server itself from faults in teh app (so bad people can't use your server to command their botnet or whatever).

while I don't use frontpage, i do do asp development pretty regularly, and it gives you many more options from a security front. check out the ms web dev essentials ide.

good luck,

---

### Post by cdenley on 2010-01-26
Regardless of how poorly that site's content may have been developed, I don't think static html content can be used to compromise a server. I didn't notice any pages which seemed to require server-side execution of any kind. If server-side scripting such as PHP, JSP, or ASP.NET were used, then certainly a competent developer would be a security requirement. However, with static content, the server just needs to be configured and maintained properly.

---

