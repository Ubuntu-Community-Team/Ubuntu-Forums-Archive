---
title: "Hula and my Webserver"
date: 2006-07-25
forum: Server Platforms
---

### Post by gdog05 on 2006-07-25
I am setting up a small private webserver, and being a complete n00b, I'm trying to use as many GUI programs as I can. I'm using 6.06, I installed XAMPP (I like it), but I ran into some snags with the mailserver. All I need is to post form mail, and I didn't realize I needed a mailserver to run form mail (I thought it could be forwarded through php or Apache settings). Please correct me if I'm wrong. 

I've seen a lot of posts of people with this problem, but I haven't been able to wean enough info yet. I installed Hula, and it sends mail through the web interface, but how do I tie it into the webserver for forms? I don't understand how this part of things works yet. A solution to the Hula problem, and pointing me to info on how it works would do me wonders. Thanks,

GDog

---

### Post by gdog05 on 2006-07-25
Did I ask the wrong question, or is this not a very widely used app? If there is another way to send PhP mail forms, or if there is a better <easy> mail server, I would be happy to learn. Thanks.

---

### Post by JoWilly on 2006-07-25
The scalix mailserver was just opensourced. Its web interfaces look very good  looking at the screenshots on scalix.com. They also have debian packages. Plugins support outlook, thunderbird, evolution,...

Todays news here:

[http://www.serverwatch.com/sreviews/article.php/3622046]("http://www.serverwatch.com/sreviews/article.php/3622046")

Thats for the interface part (which also includes mail server etc,..)


Now if you really want to run hula and need a mailserver, install postix (smtp for sending mail) and courrier (pop/imap to receive mail).

But I would definitely take a second look at scalix.

---

### Post by gdog05 on 2006-07-25
You're right. That does look good. Thanks for that, I saw that article in a feed on the side of a page, but I ignored it. I've got learnin' to do, and I really appreciate your help.

---

### Post by JoWilly on 2006-07-25
Yep, seeing what I read it seems scalix looks better and is easier to install than setting up postfix/courrier and the necessary databases.

Please report back with how it goes if you chose to try the scalix way.

---

### Post by gdog05 on 2006-07-25
Sure thing. I'm downloading it now. I will install it to see how it goes. Every time I install something I learn more. postfix/courier solution seemed a bit tough, I'm still figuring it all out. Figuring out Ubuntu and servers both has plenty of happy Eureka! moments.

---

### Post by jroc777 on 2006-08-02
How did the scalix install come out.
I am looking ot install a production mailserver,just curious/
Thanks in advance

---

### Post by gdog05 on 2006-08-02
I'm sorry to report, it didn't go well. I got things so clustered I had to wipe and clean and I'm getting ready to make another pass at it. I did hear about another mail server called Surgemail that I was gonna look into. I will keep this thread posted if I call it quits or have success.

---

### Post by gdog05 on 2006-08-02
Skip this post :)

---

### Post by erk on 2006-08-16
> **JoWilly said:**
> 

...Now if you really want to run hula and need a mailserver, install postix (smtp for sending mail) and courrier (pop/imap to receive mail).



Now you don't. the Hula package comes with POP and SMTP servers installed.

[https://wiki.ubuntu.com/Hula](https://wiki.ubuntu.com/Hula)

[http://www.hula-project.org/Installing_From_Packages](http://www.hula-project.org/Installing_From_Packages)

---

### Post by xchrisday on 2006-08-16
Just tried hula on my home server and it seemed to get stuck on spamassasin after running hulamanager after apperantly succesfully completing hula-setup. Then tried installing postfix manually etc... looks like im gonna be rebuilding this server...its a wee bit messy now.

Any additional things you need todo other then apt-get hula, hula-setup then hulamanager?

---

### Post by gdog05 on 2006-08-17
I got stuck a few times, just on various parts of the hula-setup. I had to wipe clean. I'm about ready to give up on mailservers. I just need a mail class to send form mail, so I'm actually looking into this: [pHpMailer]("http://phpmailer.sourceforge.net/"). I don't have as much time to play around with this as I did, but I'll keep the thread posted with how it went.

GDog

---

### Post by hkgonra on 2006-08-31
I am looking forward to trying out zimbra. I looked at Scalix, Hula and Zimbra and I think when I finally get around to setting up my server I will run zimbra.

---

### Post by gdog05 on 2006-08-31
Cool, I haven't heard of Zimbra, I will check it out. Thanks.

---

