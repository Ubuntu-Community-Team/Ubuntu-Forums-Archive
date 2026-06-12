---
title: "What do you think about this article on Ubuntu security?"
date: 2010-02-23
forum: Security
---

### Post by ismaelito on 2010-02-23
A friend of mine has advised me this article about Ubuntu security:
[http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/)

I have read it,it's really very interesting.
However, is it recommended to make all theses changes that have been told in this article?
Thanks

---

### Post by gdonwallace on 2010-02-23
After reading the article, I can see it in two different ways.  

1.  If you have information on your computer that you don't want anyone under and circumstance to be able to access, then by all means do those things.  It will provide another layer of security to an already secure OS

2.  If you are a little paranoid about anyone that may just jump on your computer and start looking around, or worried about someone trying to hack your computer in any way, then I would recommend any of the solutions found in that article.

For me, I don't have any of that done on my laptop.  There is nothing on my laptop that I don't care if anyone sees.  I don't have any personal documents, or information stored on it, so I don't really care.  The reason for this is how Linux manages root access.  When you first setup Ubuntu it asks for you login and creates it for you.  But that login does not have admin capability. Thus the use of the sudo command, so that you don't have to be admin all the time to do things to the computer.  By default, Windows creates the primary user and gives them admin privileges.  This is one of the things that makes windows so insecure.  Anyone that can hack and login to the computer with that login, has admin privileges, and can do what they want.

Now my machine at work has one added layer of security.  The /home directory is encrypted. There are things that I don't want others to see or access.  I chose to encrypt the /home directory at install.  Just another layer of security.

What it comes down to is personal preference.  Doing everything in that article would result in a very secure machine, but is it necessary for You secure peace of mind.

---

### Post by chiques on 2010-02-23
> **gdonwallace said:**
> After reading the article, I can see it in two different ways.  

1.  If you have information on your computer that you don't want anyone under and circumstance to be able to access, then by all means do those things.  It will provide another layer of security to an already secure OS

2.  If you are a little paranoid about anyone that may just jump on your computer and start looking around, or worried about someone trying to hack your computer in any way, then I would recommend any of the solutions found in that article.

For me, I don't have any of that done on my laptop.  There is nothing on my laptop that I don't care if anyone sees.  I don't have any personal documents, or information stored on it, so I don't really care.  The reason for this is how Linux manages root access.  When you first setup Ubuntu it asks for you login and creates it for you.  But that login does not have admin capability. Thus the use of the sudo command, so that you don't have to be admin all the time to do things to the computer.  By default, Windows creates the primary user and gives them admin privileges.  This is one of the things that makes windows so insecure.  Anyone that can hack and login to the computer with that login, has admin privileges, and can do what they want.

Now my machine at work has one added layer of security.  The /home directory is encrypted. There are things that I don't want others to see or access.  I chose to encrypt the /home directory at install.  Just another layer of security.

What it comes down to is personal preference.  Doing everything in that article would result in a very secure machine, but is it necessary for You secure peace of mind.


Thanks for the heads up regarding encryption. I've always wondered where that took place.

---

### Post by bodhi.zazen on 2010-02-23
IMO there is a bunch of misinformation and opinions on that blog.

For example, by default, openssh-server is not installed, so it makes no sense to worry about root logins. Second the root account is locked, so, with the default settings, it is not possible to log in to the root account via ssh so again this is a non issue.

Now it is true one can log into the root account in other ways (ssh keys), but this is not enabled by default (no one has a set of ssh keys to log in with).

IMO that blog falls a bit short.

I suggest you read :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

---

### Post by ismaelito on 2010-02-24
> **bodhi.zazen said:**
> IMO there is a bunch of misinformation and opinions on that blog.

For example, by default, openssh-server is not installed, so it makes no sense to worry about root logins. Second the root account is locked, so, with the default settings, it is not possible to log in to the root account via ssh so again this is a non issue.

Now it is true one can log into the root account in other ways (ssh keys), but this is not enabled by default (no one has a set of ssh keys to log in with).

IMO that blog falls a bit short.

I suggest you read :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)


Thanks for your answer, very good explanation,  so i should not make any changes.
I just want to tell you that i had already read [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")  the first day i had registered in this community :popcorn:.
I don't want to be a pain in the neck:D, i am concerned about security in internet, because i deal with some stuff related to banking, selling and buying by Internet.
Just as i said in other post, in windows i use the virtual mode, secure mode or sandbox of kaspersky internet security, i have never got any problem. 
Since i started to use linux, and according to linux' users, we don't need antivirus, antispyware , because linux is very safe, i have been looking for to learn more about security in linux.
Thanks for your help.

---

### Post by bodhi.zazen on 2010-02-24
> **ismaelito said:**
> Thanks for your answer, very good explanation,  so i should not make any changes.
I just want to tell you that i had already read [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")  the first day i had registered in this community :popcorn:.
I don't want to be a pain in the neck:D, i am concerned about security in internet, because i deal with some stuff related to banking, selling and buying by Internet.
Just as i said in other post, in windows i use the virtual mode, secure mode or sandbox of kaspersky internet security, i have never got any problem. 
Since i started to use linux, and according to linux' users, we don't need antivirus, antispyware , because linux is very safe, i have been looking for to learn more about security in linux.
Thanks for your help.

for the most part you should relax and enjoy Linux. This is not windows and the vast majority of users are fine with the defaults.

See this post :

[http://ubuntuforums.org/showpost.php?p=8620985&postcount=236](http://ubuntuforums.org/showpost.php?p=8620985&postcount=236)

In terms of security, paranoia is one thing, but changing system settings, without understanding what you are doing and why, is another. As much as possible I strongly advise you confirm any security advice you receive and as much as possible review the  technical documents rather then personal blogs.

In terms of online financial transactions, the things you need to be aware of is [Phishing](http://en.wikipedia.org/wiki/Phishing) and you should always use https (ssl).

Otherwise see :

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604") 

Privacy is another related issue. The most important issue in Privacy is physical access. If somebody has physical access to your box then can potentially read your data. Changing the default settings in /home does little as people can always boot a live CD or pull the hard drive. The best solution remains encryption.

Privacy on the internet, IMO, is not really possible. You can use things such at tor and proxies but even then I would not assume privacy.

The other problem is over the internet someone can read your data. http is not encrypted, so you will see financial institutions use ssl (https) as https encrypts your data.

Assuming you have a router and you are not running a server the possibility of a remote exploitation is almost zero. Do not user ssh or VNC or other servers unless you understand how to secure them.

You next step is to confine all network aware applications with apparmor. If you wish, you can download Zenix which has an apparmor profile enabled for all network aware applications enabled by default.

[http://zenix-os.net/](http://zenix-os.net/)

So while paranoia is healthy, running around reading personal blogs and changing system settings without understanding what you are doing and why is not, as I explained in my comments on ssh. 

Running through that blog point by point and debating the issue will not make you more secure either.

You will need to read and understand why the advice is given and then decide for yourself if you wish to implement it, but do not blindly change the security settings.

---

### Post by Sir Jasper on 2010-02-24
Hi bodhi and all,

I have just updated my Firefox add-on Flagfox to v 4.0.0 and as it has some security aspects (e.g. Geotool, SiteAdvisor and WoT (via additional Options) I wondered if it might be of interest.

[[img]http://f.imagehost.org/t/0116/Flagfox.jpg[/img]](http://f.imagehost.org/view/0116/Flagfox)

My regards

Added:
My apology - I had mistakenly typed ¨Fireflag¨, but I have now corrected the above name to ¨Flagfox¨

---

### Post by bodhi.zazen on 2010-02-24
> **Sir Jasper said:**
> Hi bodhi and all,

I have just updated my Firefox add-on Fireflag to v 4.0.0 and as it has some security aspects (e.g. Geotool, SiteAdvisor and WoT (via additional Options) I wondered if it might be of interest.

[[IMG]http://f.imagehost.org/t/0116/Flagfox.jpg[/IMG]]("http://f.imagehost.org/view/0116/Flagfox")

My regards

Tank you. I have tried those things. Very  cool.

---

### Post by ismaelito on 2010-02-25
@[[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054"), i want to use your profile of firefox 3.6, i have read the Jamie Strandboge's profile for 3.5 and yours, there are few differences.
I used this command : ```
sudo complain firefox
```Now firefox 3.6 is working.
Do you think would it work for me?, or i change the first line of Strandboge's profile
 /usr/lib/firefox-3.5.*/firefox flags=(complain) {  to 
/usr/lib/firefox-3.6 /firefox flags=(complain) {  and keep this one.
Thanks.

In reality, i am looking for to sandbox Firefox with AppArmor.

---

### Post by bodhi.zazen on 2010-02-25
If you want to manually tweak apparmor you will need to do some reading, I suggest you start with the apparmor thread.

My profile is written for firefox 3.6, downloaded from mozilla, and installed into /usr/local/firefox (you will see the path in the profile).

So if you install firefox 3.6 the same way, my profile will work for you. If you installed firefox in some other way, or used a .deb, you will need to adjust my profile.

---

### Post by ismaelito on 2010-02-25
> **bodhi.zazen said:**
> If you want to manually tweak apparmor you will need to do some reading, I suggest you start with the apparmor thread.

My profile is written for firefox 3.6, downloaded from mozilla, and installed into /usr/local/firefox (you will see the path in the profile).

So if you install firefox 3.6 the same way, my profile will work for you. If you installed firefox in some other way, or used a .deb, you will need to adjust my profile.

I installed Firefox following: 
[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)
What i am going to do, is to download firefox from:
[http://www.mozilla-europe.org/es/firefox/](http://www.mozilla-europe.org/es/firefox/)
And install it in usr/local, after i will use your profile.

---

### Post by bodhi.zazen on 2010-02-25
I found it to be fairly straight forward to go that route (direct download from mozilla), but if you have problems, let  me know.

---

