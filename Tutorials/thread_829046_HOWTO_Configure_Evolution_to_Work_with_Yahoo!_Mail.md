---
title: "HOWTO: Configure Evolution to Work with Yahoo! Mail"
date: 2008-06-14
forum: Tutorials
---

### Post by mdpalow on 2008-06-14
Hi Everyone,

Sorry if this already exists, but I didn't see it if it does.

Would like to just put together a quick little tutorial on how you can use Evolution to access your Yahoo! e-mail account.

Before I begin, let me say that at this time, you have to pay for a PLUS mail account in order to pop3 it with Evolution or any other e-mail tool. 
****************************************************************************

1. Open Evolution and click EDIT -> PREFERENCES from the menu.

2. On the left, ensure MAIL ACCOUNTS is high-lighted. Click ADD.

3. Click FORWARD.

4. Enter whatever personal information you like.

5. Select [COLOR="Red"]POP[/COLOR] for Server Type.

Now add the following for RECEIVING EMAIL

[COLOR="Red"]SERVER: plus.pop.mail.yahoo.com:995 [COLOR="Black"](Notice port number at the end)
[/COLOR]
Username: your Yahoo! username _WITHOUT_ @yahoo.com at the end

Use Secure Connection: SSL Encryption

Authentication Type: PASSWORD

Remember Password: Checked    (optional)[/COLOR]


6. Click FORWARD button.

7. Set the next options to your liking.

8. Click FORWARD.

Now add the following for SENDING EMAIL

[COLOR="Red"]Server Type: SMTP

SERVER:  plus.smtp.mail.yahoo.com:465 [COLOR="Black"](Notice port number at the end)[/COLOR]

Server requires authentication: Check this box

Use Secure Connection: SSL Encryption

Authentication: Plain

Username: your username _WITHOUT_ the @yahoo.com[/COLOR]


9. Click FORWARD.

10. Enter a name for this setup. I use: Yahoo!


Click apply and your done.

You won't be asked for your password until you actually go to send/receive e-mail for the first time.

Good luck and hope this helps...

---

### Post by bhadotia on 2008-08-02
Thanks for the nice howto:KS

---

### Post by nnamdi on 2008-08-02
Great !!! thanks for the information man

---

### Post by rebelrouser9 on 2008-08-06
Does anyone know if there is a way of doing the same thing but WITHOUT a PLUS mail account?

---

### Post by sebastian.gasparetti on 2009-08-22
Awesome! Thanks.

---

### Post by Levo on 2009-09-22
Nice HOWTO! Thanks!

---

### Post by wnelson on 2009-09-22
Use Thunderbird with webmail/yahoo extensions.

[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

---

### Post by bbjeg on 2009-12-03
To get this to work without a plus account, remove "plus." from the tutorial. Both of them. It worked for me.

---

### Post by zkphill on 2009-12-29
I tried using the setup instructions listed above and this is the message I got from evolution.   

      Unable to connect to POP server pop.mail.yahoo.com.
      error sending password:-ERR[SYS/PERM] pop not allowed for user.

---

### Post by Mahngiel on 2009-12-29
"POP not allowed."  I do believe Yahoo! is persistent in it's regard to keep their email traffic on their own site, and will now allow you to divert it.

---

### Post by zkphill on 2009-12-30
One way of getting yahoo mail on evolution is to have a gmail account set to import your
email from the yahoo account. Then all you have to do is use evolution to access your gmail account and you will get both gmail and yahoo. By the way, if you have spam block
activated on the yahoo account some of your messages will not come through to gmail.

---

### Post by m3owner on 2010-01-02
> **wnelson said:**
> Use Thunderbird with webmail/yahoo extensions.

[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

I'm a noob and after a long trial I got T-bird installed. I would appreciate if someone can give me a step by step of how to get the webmail and Yahoo extensions installed.

Without them I get an error in T-bird that my account info is wrong although I know my name and password are correct. I believe the error is due to Yahoo not accepting my POP and presume the yahoo extension makes it work.

I did multiple posts yesterday in the "how can I upgrade thunderbird 3" forum, but haven't gotten any responses to inquiries today

---

### Post by migel_wimtore on 2010-01-03
Big up zkphill, that works indeed. But, will it continue to redirect new mail after 30 days?

Thanks.

---

### Post by zkphill on 2010-01-04
Apparently it doesn't. My gmail account hasn't been able to get any new messages from my yahoo account.

---

### Post by migel_wimtore on 2010-01-04
Shame. So, basically the Gmail fix just imports your history, which soon becomes out of date. :(

---

### Post by bijeeshvs on 2010-02-11
I dont have any plus account with yahoo, but my htc successfully retrieves mail from yahoo using its native email client with settings :
server : imap.mail.yahoo.com
imap4
but the same settings wont work with evolution, any  ideas??????????????

---

### Post by chehalem on 2010-06-29
if you have an older yahoo mail account you can set it to Asia and get free POP account.  this worked great for me with evolution.

[http://picobit.wordpress.com/2009/04/10/yahoo-mail-free-pop-access/](http://picobit.wordpress.com/2009/04/10/yahoo-mail-free-pop-access/)

this site may also be helpful for folks wanting to use thunderbird

[http://ubuntuforums.org/showthread.php?t=1372937](http://ubuntuforums.org/showthread.php?t=1372937)

---

### Post by chehalem on 2010-06-29
I also discovered i had to take the word "plus" out of the outgoing server configuration to make it work for me.

smtp.mail.yahoo.com:465

instead of...

plus.smtp.mail.yahoo.com:465

---

### Post by CrazyDavy on 2010-07-16
Still excellent information!  Thanks:P

---

### Post by thedomed on 2010-09-14
Thanks for that, I was about to give up on evolution

---

### Post by wilee-nilee on 2010-09-14
If you don't want to pay for yahoo pop, it is rather cheap though, there is a FF add on call yahoo mail notifier that does it for free.

---

### Post by kcn_viper on 2010-09-27
imap and smtp now work for free with yahoo mail. I was able to do this with evolution mail client.
1. imap.mail.yahoo.com
SSL Encryption

2. smtp.mail.yahoo.com
Server requires authentication
SSL Encryption
Authentication Type: PLAIN

---

### Post by dmp2010 on 2010-10-10
Not working with AT&T yahoo. I tried without plus. I tried without the port numbers 995 and 465. Please help.

---

### Post by VanceVEP72 on 2010-10-19
This is how I got my US Yahoo! Mail to work in Evolution...

Receiving Email Tab:
Server Type: IMAP+
Server: imap.mail.yahoo.com
Username: Yahoo! ID WITHOUT "@yahoo.com"
Security: SSL encryption
Authentication Type: Password
check mark: Remember Password

Receiving Options Tab:
checkmark: Check for new messages in all folders

Sending Email Tab:
Server Type: SMTP
Server: smtp.mail.yahoo.com
checkmark: Server requires authentication
Security: SSL encryption
Type: PLAIN
Username: Yahoo! username WITHOUT "@yahoo.com"
checkmark: Remember password

---

### Post by outleradam on 2010-10-20
^^ that worked.  It took a while to do anything,  but it worked.

---

### Post by TheTinyt1 on 2010-10-27
I had no problem with this. It worked flawlessly. Thanks for the help...

Now I have 2 questions.  

Is there any way to copy your folders to evolution from yahoo?

How do I import my contacts from yahoo or can I?

Thanks again for the great work...

Bright Blessings
Charles Ellibee
:KS:KS:KS

---

### Post by richardandrews on 2011-02-09
Thanks for the guide, very helpful.I don't pay for plus account and this works fine.I tried this a few weeks back and couldn't get it to work, I only just realised that you have to go into your account online and make sure that pop forwarding is checked (I wondered why my phone stopped receiving email, I was blaming 3)Go options-more options-pop and forwarding.I hope this helps someone else.

---

### Post by Wesley Dawson on 2011-02-09
Yeah I figured this out earlier... it sucks that yahoo makes you pay to pop your account.

---

### Post by r.osmanov on 2011-02-27
Failed for me. It seems, it requires a "plus" account. 
I've imported Yahoo! account to Gmail.

---

### Post by KG4UJD on 2011-03-02
Thanks worked great

---

### Post by znobrdr on 2011-04-24
22Apr2011 - Works perfect Ubuntu 10.10 ! Thanks! Yahoo Mail Plus ! .):P

---

### Post by bohemian9485 on 2011-09-16
I tried this method with and without "plus" and met with zero success, after some googling, it appears that you need to enable POP from your Yahoo email account for this to work in Evolution.

From your email account, go to Options => Mail Options and select POP & Forwarding. Click the Allow Your Yahoo! Mail to be POPed option and save your changes. Presto, now you can see all your mails inside Evolution :D

---

### Post by dcstar on 2011-12-22
> **bohemian9485 said:**
> I tried this method with and without "plus" and met with zero success, after some googling, it appears that you need to enable POP from your Yahoo email account for this to work in Evolution.

From your email account, go to Options => Mail Options and select POP & Forwarding. Click the Allow Your Yahoo! Mail to be POPed option and save your changes. Presto, now you can see all your mails inside Evolution :D

This is basically what you need to do for Evolution to use Yahoo IMAP:

[http://help.yahoo.com/l/us/yahoo/mobile/comms/mail/imap-01.html](http://help.yahoo.com/l/us/yahoo/mobile/comms/mail/imap-01.html)

---

