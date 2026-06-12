---
title: "Is there a simple way to implement a mail server?"
date: 2011-02-21
forum: Server Platforms
---

### Post by insafeuste on 2011-02-21
I have literally spent 13 hours straight trying to fix this problem so I will try to explain my situation in as concise a manner as possible, hoping not to ommit any important detals. I am putting a php contact form on my webpage that sends messages directly from the page to my email address. This script has worked in the past, but unbeknownst to me that is because my previous server was running a mail transfer client that handled php's mail() function through smtp. The web server I am using now is a home machine configured with ubuntu running php/apache but there is nothing to handle mail. My contact form says the message has been sent, but it never arrives to my inbox.
 
Following forums, I installed sendmail and verified that smtp was running on port 25, but the form would then hang for over a minute upon submission(and messages still would not be delivered). I then tried exim4 as a mail transfer agent which solved the hanging, but messages still werent delivered. From my reading it appears this could have something to do with my hosts file, but I am unsure how this needs to be configured (pretty new to all this and I seem to have bitten off more than I can chew). 
 
I eventually configured exim4 to use the smarthost feature for outgoing mail, using my gmail account's smtp server (following a tutorial). My exim log file produces no errors, but messages from my contact form still are not delivered. This has turned out to be a huge, hair tearing situation and I'm at a loss on what to do next. I'm just not ready to give up and start paying monthly for a webhost again just for this contact form, so I'd really love any suggestions on what i need should try next. Thank you!

---

### Post by kg4cna on 2011-02-21
Most ISP's block port 25 on their customer's connections. I would check with them and make sure it's not being blocked. It will not matter what kind of MTA you use if the port is blocked, you'll get no email from the form submission.

I use a php contact form on my in-home webserver...but it's not the desktop I use daily. I use Postfix on it for sending mail. My ISP doesn't block my port 25 so I get my form submissions.

A~

---

### Post by insafeuste on 2011-02-21
Thank you for the quick reply. I just forwarded port 25 in my router configuration to make sure that wasnt the issue, then used canyouseeme.org to confirm that my port is not blocked by my isp. It seems my problem lies in the configuration of my mail server.. i looked a bit more closely at my exim4 log file and i'm getting an error saying that the 'message is frozen'. Maybe I shall give posix a try, its uplifting to know you got your contact form working with it :).

---

### Post by garfonzo on 2011-02-21
Interestingly, I just finished creating a website that has a form on it. This form also is to be emailed to me and I also encountered **extreme frustration** trying to have that form emailed to me. I spent all weekend trying to figure it out. 

I did find a solution, though. 

Instead of installing and configuring a mail server and having my server handle the email (which was possible since my internet connection is a business line and thus, no ports are blocked) I decided to use Gmail as my SMTP server. Yup, you can piggy back on Gmail to have it send your email for you. 

I wrote my script in Python, but I think the idea is language-independant. You set up a session within the script, use your Gmail login name and password, and send your email off that way. Of course, this assumes you have a Gmail account. If you don't have one, create one just for this. My only gripe about this method is that you have to store your password in plain text in your script.

Do some Google searches on "Use Gmail as SMTP server". I found enough examples to show me how to do it and make it work. Here are a few places I used as guidance, but they are Python specific

[Link one]("http://www.mkyong.com/python/how-do-send-email-in-python-via-smtplib/")
[Link two]("http://kutuma.blogspot.com/2007/08/sending-emails-via-gmail-with-python.html")
[Link three]("http://segfault.in/2010/12/sending-gmail-from-python/")
[Link four]("http://www.example-code.com/python/python-gmail.asp")

I now have a wonderfull contact form which emails two people and BCC's a third person, all through Gmail's smtp. 

The other benefit of this solution is that I don't have to install a messy mail server (I also read through forum threads of setting up Postfix, or Exim4 *shudder*). I don't want to deal with a mail server because I have a single contact form that needs email functionality.

Hope this brings you closer to a solution!

---

### Post by HermanAB on 2011-02-21
Howdy,

To answer the original question, setting up an email server is very easy indeed:
[http://www.citadel.org/doku.php?id=installation:start](http://www.citadel.org/doku.php?id=installation:start)

It takes about 20 minutes to run the Easy Install script and then it Just Works (TM).

---

### Post by cariboo on 2011-02-21
If you've already got a domain name, and only need up to 50 email addresses, have a look at [Google Apps]("http://www.google.com/apps/intl/en/group/index.html"). I had email setup in less than 15 minutes. You don't have to worry about blocked ports, and  the client setup is pretty easy.

---

### Post by insafeuste on 2011-02-21
Thank you for all the suggestions, I wish I had posted sooner.. I'm going to take a look at googleapps as that seems like the most simple solution, and it comes with a tutorial on setting up my dns. 
 
@Garfonzo, its good to see I wasn't alone in facing this frustrating problem. As mentioned above, I setup my exim4 agent to use gmail's smtp server, but messages still were not getting through. I don't know python, but I found a library called phpmailer which would essentially enable me to send my contact form through my gmail account through a php script on my directory. It seems though that I would have to rewrite my contact form and as that took me quite a while to setup (getting captchas to work took was a few hours alone..) I will keep this option as last resort in case google apps doesnt do what i need. 
 
I'm still curious about what I needed to put in my hosts file for my current mail agent to work, assuming that was part of the problem, but I think i'll just start a new thread to keep this one focused on the different mail server options available.

---

### Post by kemra on 2011-02-22
If you're still looking at using your own server have you ensured that /etc/php5/php.ini contains a referance to your mail server?

It should have a section something like:

```
[mail function]
sendmail_path = /usr/sbin/sendmail -t
```

I don't have a sendmail install of my own (my own web server is hosted externally so i don't have access to the php.ini file to double check the details) so can't check but you should only need the above.

---

