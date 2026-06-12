---
title: "Setting up a quick MAIL server"
date: 2008-01-26
forum: Server Platforms
---

### Post by guitarman on 2008-01-26
Hi,
does anyone know of a quick way to setup a mail server on Ubuntu server. I have 2 older IBM machines, one which I set up as a web and the other I would like to set up as a Mail server.  There seems to be so many different procedures, but I'm just looking for a quick and easy step by step procedure that I can use to be up ASAP. The domain I have is being redirected using no-ip.com so would I need to also do a MX record redirect too?

thanks,

---

### Post by p_quarles on 2008-01-26
Moved to the Servers & Security sub-forum.

---

### Post by HermanAB on 2008-01-26
Yes, the quickest way to set up a fully functional mail server is with Citadel.  It takes about 20 minutes: [http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)

OK, 40 minutes, if you want Spam Assassin and ClamAV too.

However, you absolutely have to have the DNS working properly for any mail server to work.  Pretty much every head banging problem with mail is due to a badly configured DNS.

Cheers,

Herman

---

### Post by guitarman on 2008-01-27
Hi Herman,
Thanks for this.  I wen to install all the Citadel prerequisists as per their web site and when i went to do the Easy Install, i type the following at my prompt (using root):

 su curl [http://easyinstall.citadel.org/install](http://easyinstall.citadel.org/install) | sh 

but keep getting this error:

 Unknown id: curl


Any idea what I am missing?

thanks

---

### Post by p_quarles on 2008-01-27
You'll need to install curl first:
```
apt-get install curl
```

Or you can follow the wget tutorials given in the tutorial: that's installed by default.

---

### Post by tlcoffee on 2008-01-27
You can install Postfix fast and easy.

```

sudo apt-get install postfix

```

Quick guide: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

---

### Post by HermanAB on 2008-01-27
"You can install Postfix fast and easy."

I agree that you can install Postfix fast and easy, but Postfix is just one little Lego block in a mail server (postfix, dovecot, apache, roundcube, SSL, MySQL, yadda, yadda).  Getting all the rest to work takes an awfully long time, while Citadel has one All Encompasing Orange Catholic Holy Easy Install Script that provides a quick and straight road to mail salvation...

---

### Post by tlcoffee on 2008-01-27
mhmm

Well, I understand that some people require pop3 + webmail (dovecot, roundcube, SSL is already apart of the MTA) and those require apache and mysql. However, he didn't ask for that. A mail server is an MTA.

He said he setup one box as a webserver. I'm going to assume that he also put mysql on there and if he needs webmail for it, he's already got what he needs on that server.

I don't think he understands exactly what he's getting into with such a large package as Citadel.

```

[LIST]
[*]email
[*]calendaring/scheduling
[*]address books
[*]bulletin boards
[*]mailing list server
[*]instant messaging
[*]multiple domain support
[*]modern AJAX-style web interface[/LIST]
```

Your right, it is an all-around all-encompassing package. Very nice indeed.

There is a lot to learn there if something goes wrong or adds components he won't need or request.

However, that may just be what he was actually wanting.

---

### Post by artcancro on 2008-01-28
> **guitarman said:**
> 
 su curl [http://easyinstall.citadel.org/install](http://easyinstall.citadel.org/install) | sh 

but keep getting this error:

 Unknown id: curl

I think you wanted "sudo", not "su".   Personally I would just log in as root, but if you insist on doing it the sudo way, it's

curl [http://easyinstall.citadel.org/install](http://easyinstall.citadel.org/install) | sudo sh

---

### Post by googlah on 2008-01-28
I would definitely look into Postfix the first thing I do. I've always had Postfix, and it's really simple to get it to work.

Strange enough, I don't even have a MX-record, I only have a A-record. Really strange I know, but it does work. Just apt-get install postfix and go from there. :)

---

### Post by guitarman on 2008-01-28
folks,
thanks for all the help.  Indeed I have 2 servers (one which I dedicated to simply apache as my web server and a second one which I wanted to dedicate as a mail server).  In fact I wanted to set up Postfix initially along with Squirrel Mail, however when I saw the reference to Citadel, I figured that this would be a turnkey solution that would save me a lot of configuring.  I did however use Artcancro advise, but I still get the following without any success:

--------------------------------------------------------------------------------
                                 Dload  Upload   Total   Spent    Left  Speed
100 13105  100 13105    0     0  44732      0 --:--:-- --:--:-- --:--:--  112k

guitarman@ubuntu-mail:~$ curl [http://easyinstall.citadel.org/install](http://easyinstall.citadel.org/install) | sudo sh
Password:  % Total    % Received % Xferd  Average Speed   Time    Time     Time     Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 13105  100 13105    0     0  42315      0 --:--:-- --:--:-- --:--:-- 77088

guitarman@ubuntu-mail:~$ curl [http://easyinstall.citadel.org/install](http://easyinstall.citadel.org/install) | sudo sh
Password:  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 13105  100 13105    0     0  53204      0 --:--:-- --:--:-- --:--:--  118k
-------------------------------------------------------------------------------

Not sure what it is that I am doing wrong.  I just want to set up a quick email server so that I can host the sending and receiving of emails from the domain name that I registered for my wife and that we can retrieve them remotely - hence Squirrel mail.

Should I stick with Citadel? I also looked at the opensource version of Zimbra (but this needs a larger server with more memory).  The server i got is older and I do not want to upgrade it just yet.

I registered with godaddy.com and redirect with no-ip.com and my webserver works great. Now I need to just configure the mail server.

thanks again,

---

### Post by DDuong on 2008-01-29
Hello,

This is the tutorial I followed to get my mail server going.  Of course I had to play with my DNS server to get it working properly.

[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10)

I hope this helps!

---

