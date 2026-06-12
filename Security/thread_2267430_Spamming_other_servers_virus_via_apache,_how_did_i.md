---
title: "Spamming other servers virus via apache, how did it get in, and how to get it out?"
date: 2015-03-01
forum: Security
---

### Post by GiantCowFilms on 2015-03-01
[B]Background:
[/B]I've only ever used windows until I spun up my first VPS using ubuntu, and know almost nothing about it. I'm not terrible experienced, but I'm going to try fix this issue
[B]Issue:
[/B]Yesterday (2/28/15) I got a notice from my hosting company about an abuse complaint, accusing my server of spamming peoples comments. After some hours doing non-related stuff, I saw and addressed the complaint.  I immediately went to the only log file I know about, the general Apache log inside it where thousands upon thousands of messages like this (Obviously modified to protect information, also several different IPs were at it at the same time):

[FONT=lucida console]85.XX.XXX.155 - - [28/Feb/2015:08:20:20 -0700] "GET [http://www.example.com/not/a/site/I-know/postComment](http://www.example.com/not/a/site/I-know/postComment) HTTP/1.1" 200 12621 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.111 Safari/537.36"[/FONT]

:shock: *gulp* something went wrong. I've turned off the server for now... but I need to get it running again soon.

I have no idea what information is relevant, or how to get it, feel free to ask for info, just tell me where to find it...

My main questions:
 - What is this attack, do I have a virus on my server or how is this working
 - If A virus got on my server, how do I find/patch the hole
 - How to I use blacklists to block IPs, all the offending ones where known spammers
 - Is there anything I should know... where to look for help, what this type of attack is called, to help me conduct research on this... I've spend hours on google with no avail. assume I know nothing.

---

### Post by fugu2 on 2015-03-01
are you running any kind of a preconfigured website on your web server (wordpress, joomla, etc)? have you been diligent with updates for the server? my advice, backup && reformat && reinstall.

---

### Post by GiantCowFilms on 2015-03-01
No, all my own code... I'm not sure about updating though... I don't think I've ever knowingly updated the server (how do I do that)... yes, it just might be easier to go from a clean slate. My only fear is that because I don't know what I'm doing the hole will still be there and they will just get back in again and again. I really need to know what kind of an attack is allowing them to do this and how they got in then yes, I can use a different setup.

---

### Post by lisati on 2015-03-01
I wouldn't worry too much about the lines that look like this:
> 85.XX.XXX.155 - - [28/Feb/2015:08:20:20 -0700] "[COLOR="#FF0000"]GET[/COLOR] [http://www.example.com/not/a/site/I-know/postComment](http://www.example.com/not/a/site/I-know/postComment) HTTP/1.1" 200 12621 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/40.0.2214.111 Safari/537.36"
That is normal, and indicates that someone is browsing your website.

I'm wondering what is meant by your reference to "spamming" - is it sending out lots unwanted emails? Does your website have some kind of sign-up process? If so, you might need to look at tightening up the registration process to use only verified email addresses. The basic idea is to not blindly send out emails to any old email address (which could be forged) but to send out ONE email requesting the "owner" of the email address confirm that they want to receive emails from you. Until this confirmation is received (which could be by clicking on a link) you shouldn't send any more emails to that person.

---

### Post by fugu2 on 2015-03-01
I know the Ubuntu server well enough but I've never used it as a vps before. If you can add a crontab entry, you might consider adding 
```

$ sudo crontab -e

```
Then add
```

x y * * * apt-get update && apt-get -y upgrade && test -e /var/run/reboot-required && shutdown -r now

```
where x is a minutes, from 0 to 59 (try not to use 0 to not overload the update servers)
and y is an hours, from 0 to 23 (try not to use 0 to not overload the update servers)
This will check for updates once a day, install updates that it finds, check if the system needs to be rebooted after the updates, then restart if it needs to
Edit: fix typo

---

### Post by GiantCowFilms on 2015-03-01
Its sending POST and GET requests to other websites, not anything I own, in an attempt to spam these websites (the body of the comment request is trying to *sell* car insures and *other stuff*). Its basically being used to spam other peoples comments against my will. Furthermore, this is *not *normal usage. I received 4000 of these since yesterday morning, when the expected user base should be a small two digit number, I mean I only launched less then a week ago, and this was designed for a specific small group of people. At the current rate of requests 4000k perday, I'd see alot more usage kinds of usage.

I got auto-flagged by a post2ban system, specifically [https://www.blocklist.de/](https://www.blocklist.de/) , who notified my hosting company

---

### Post by GiantCowFilms on 2015-03-01
I don't need to automate it (in fact that could be a problem), but thank you, I will set a reminder to updated it regularly.

---

### Post by fugu2 on 2015-03-01
if you have a backup of your site, you can run a diif  of your current site and the backup to see what is different (possibly if the problem is at the application layer) ```
$ diff -u -r /path/to/copy/of/backup /path/to/changed/site
```

---

### Post by GiantCowFilms on 2015-03-01
I looked everywhere there, checked it against my local copy! its outside of /var/www/

---

### Post by lisati on 2015-03-01
> **GiantCowFilms said:**
> Its sending POST and GET requests to other websites, not anything I own, in an attempt to spam these websites (the body of the comment request is trying to *sell* car insures and *other stuff*). I

In a word: [backlinks]("http://en.wikipedia.org/wiki/Backlink").

If you have comments enabled, you might want to disable or restrict who can post comments on your site.

edit:You might also want to check to see if there's anything on your site that you didn't put there. Look for "strange" files.

---

### Post by fugu2 on 2015-03-01
just because there is no changed files between your backup and current website, doesn't necessarily mean the problem absolutely is outside of /var/www, but it probably is. I would think XSS and CSRF would show up in the apache logs, but those could be possible problems especially if you wrote the site yourself (it can be easy for 1 person to miss some mistakes), and they would not need to alter any file on the website.  If it is outside /var/www, then its possible someone got in from an other open service, maybe ssh server is running, maybe someone had physical access to the machine, etc. Without more information is hard to tell. I tend to believe the problem probably lies in /var/www or in apache itself, though, because the problem is leaving entries in the apache.log file.

---

### Post by GiantCowFilms on 2015-03-01
I do have a file upload form... shouldn't be able to do that, but maybe. I know why they are doing it, SEO back links. 

PS
These are other people comments, not mine

---

### Post by fugu2 on 2015-03-01
you might want to do a web search for 'file inclusion vulnerability' which might show you how it works, and how you might fix that problem if thats what you have.

---

### Post by GiantCowFilms on 2015-03-01
In the end it was a messed up proxy pass to node... where it wasn't locked to a domain, and they could use it for whatever the felt like, like spamming for backlinks.

---

