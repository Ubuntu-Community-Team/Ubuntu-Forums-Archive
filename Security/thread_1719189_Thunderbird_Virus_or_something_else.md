---
title: "Thunderbird Virus or something else ??"
date: 2011-04-01
forum: Security
---

### Post by MadMonkey1966 on 2011-04-01
I have been using Ubuntu for a couple of months now and love it. I also use Thunderbird as my E-mail program.

The last few weeks i have been getting strange mail, i just thought spam. They contained all sorts of stuff, some were just gibberish. At the same time i got mail coming back to me that i had not sent, yet it had my email on the returned mail as if i had sent it. Now i have had friends getting mail, that again i have not sent them.

So, basically, it looks like i am receiving mail from somewhere, which is reading email addresses in my Inbox and then automatically forwarding itself to others.

I have no Anti-virus software as i was advised there in no need with Ubuntu.

Anyone any ideas of how to stop this, and to cure if possible. It is not really effecting me, but when my family and friends are getting hassle because of it, there's a problem.

What should i be looking for, and what can i do anyone :confused:

---

### Post by IHeequ5i on 2011-04-01
Sounds to me like your email address has been hijacked. Do you use Yahoo, Gmail, or something like that?

---

### Post by MadMonkey1966 on 2011-04-01
Thanks for the quick reply :)

Well, its a GMail addy i have. Is there anything i can do about it, i didnt think i would have a problem with GMail.

What is crazy, i sthat some of the mail ready total rubbish, some in chinese and some just rubbish about Xmas.

Is there anything i can do ? I have tried filtering it out, as Thunderbird is good at that, but it seems to forward these emails before the filters get a chance to run

---

### Post by ayenack on 2011-04-01
hello MadMonkey1966.

First thing you should do is tell all the people in your E-mail list not to open any mails from you as the mail may contain malware that may infect their computers.

Then you should check the google forums for hacked accounts and help. You could just try changing the password or, if you have to, close the account and create a new account.

Check this out for a quick guide. It's not bad.

[http://www.friedbeef.com/how-to-check-if-your-gmail-account-has-been-hacked/](http://www.friedbeef.com/how-to-check-if-your-gmail-account-has-been-hacked/)

Also it might be an idea to install rkhunter just to check your actual computer has not been compromised.

sudo apt-get install rkhunter

Then update it.

sudo rkhunter --update

Then to run.

sudo rkhunter -c -sk

---

### Post by Old_Man_Unix on 2011-04-01
> **MadMonkey1966 said:**
> Thanks for the quick reply :)

Well, its a GMail addy i have. Is there anything i can do about it,.

Not much.  Your email (Gmail) address has been harvested for one of the many spam lists that are circulating around.  

> **MadMonkey1966 said:**
> i didnt think i would have a problem with GMail.

Why would you think that?  ANY email address can be harvested.

 Sometimes, an address  will get hooked if it is similar to another one, e.g, same name in a different domain.

Usually, though, your address is harvested through a web site where you provided it.   The best way to avoid this is to keep your address private - or set up multiple email acounts for different purposes

Eventually, the Gmail anti-spam will probably pick up this spammer, but until then....


> **MadMonkey1966 said:**
> Is there anything i can do ? I have tried filtering it out, as Thunderbird is good at that, but it seems to forward these emails before the filters get a chance to run

As was said in a previous response, it has nothing to do with Thunderbird - or any other mail client.  It's  very doubtful that anything happened to your client.  That's not the way these things work - they are very good at spoofing mail headers.

---

### Post by uRock on 2011-04-01
Moved to Security Discussions.

---

### Post by MadMonkey1966 on 2011-04-01
Thanks for that information, i will go through it all and let you know.

Sorry for wrong board, i was always told to post there first :)

---

### Post by MadMonkey1966 on 2011-04-01
> **ayenack said:**
> hello MadMonkey1966.

First thing you should do is tell all the people in your E-mail list not to open any mails from you as the mail may contain malware that may infect their computers.

Then you should check the google forums for hacked accounts and help. You could just try changing the password or, if you have to, close the account and create a new account.

Check this out for a quick guide. It's not bad.

[http://www.friedbeef.com/how-to-check-if-your-gmail-account-has-been-hacked/](http://www.friedbeef.com/how-to-check-if-your-gmail-account-has-been-hacked/)

Also it might be an idea to install rkhunter just to check your actual computer has not been compromised.

sudo apt-get install rkhunter

Then update it.

sudo rkhunter --update

Then to run.

sudo rkhunter -c -sk
I ran rkhunter and everything seems ok, apart from the last thing it printed

> One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)


i tried to get into have a look, but it says access denied :(

just reading the link you suggested

---

### Post by brian_p on 2011-04-01
> **ayenack said:**
> 

Also it might be an idea to install rkhunter just to check your actual computer has not been compromised.

It's an idea but not a good one.

---

### Post by cariboo on 2011-04-01
> **MadMonkey1966 said:**
> I ran rkhunter and everything seems ok, apart from the last thing it printed



i tried to get into have a look, but it says access denied :(

just reading the link you suggested

You need to be root, to view the rkhunter log

---

### Post by Rasa1111 on 2011-04-01
Gmail is probably the culprit.
I stopped using it a year or two ago,
just because of the problems I would often read about..
Then... before i did stop using it..
I could no longer login to my gmail
\Nothing I did would get me in, like my password never existed or something. 

Thats when i called it quits..
and shortly after I read a post here about "GMX mail" and how good it was.. So i checked out GMX and been using it ever since.
I just made sure to get all my contacts, and let all my 'regular' contacts have the new email and told them to delete the gmail addy. 

No problems getting it in thunderbird either. 
easiest email client setup Ive done yet. :)

hope it can help you.
good luck

---

### Post by MadMonkey1966 on 2011-04-01
Thanks for all the help. I have signed up on mail.com for one of there address's, and linked that to Thunderbird.

Think i will create another just for web use and keep personal separate. It will mean hassle change all forums and sites, but i will do it over time. What a pain.....

thanks again everyone :P

---

### Post by ayenack on 2011-04-01
To view the rkhunter log open a terminal and type this.

sudo nano /var/log/rkhunter.log

To exit press ctrl+x and it'll return you to terminal. There are some warnings you can probably ignore. If you google any warnings it'll give you some info on them.

Like everyone else I also think this is down to your gmail account being broken into you should try the link I posted in my earlier post also to check it out.

---

### Post by Rasa1111 on 2011-04-02
mail.com has gone to crap the past year or two. 
They used to be great, and I loved it..
Until they merged with AOL. : / lol
Now it's just as bad as AOL.

GMX is where it's at.

---

### Post by SeijiSensei on 2011-04-03
> **MadMonkey1966 said:**
> The last few weeks i have been getting strange mail, i just thought spam. They contained all sorts of stuff, some were just gibberish. At the same time i got mail coming back to me that i had not sent, yet it had my email on the returned mail as if i had sent it. Now i have had friends getting mail, that again i have not sent them.

These are all common spamming tricks.  For instance, if I know that [email]someone@example.com[/email] is a valid address, I can forge the From: header to send mail From: that address To: that address.

However the issue with your friends receiving this junk suggests your address book was hijacked.

Whenever you get a suspicious message, the very first thing to do, if you're running Thunderbird, is to use "View > Message Source" to see the complete set of headers that log how the message was delivered to you.  The "Received" headers list each machine the message passed through in reverse order.  One obvious identifier is that a message allegedly sent by you didn't actually originate on your mail provider's server.  

Every single aspect of an email message can be easily forged; the method of delivery as shown in Received headers much less so.

---

