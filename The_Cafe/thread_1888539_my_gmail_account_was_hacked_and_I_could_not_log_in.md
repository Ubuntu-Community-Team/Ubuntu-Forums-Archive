---
title: "my gmail account was hacked and I could not log in until"
date: 2011-11-29
forum: The Cafe
---

### Post by sdowney717 on 2011-11-29
I had a text message sent to the phone.
And had to think of a new password.

Then looking at the login history, someone in Japan had accessed my account.
What is to keep someone from changing your password and then stealing your email account? I am curious as to how they got the password. Earlier this year my hotmail account was also hijacked and some emails sent to those in my contact list.


gmail notified me of suspicious activity and here it is.
> Browser	 Japan (114.48.44.7)	 Nov 26 (3 days ago)


looking I see one email was sent that day which I did not send and here it is
> my name
Nov 26 (4 days ago)

to crow, hammerheads1962, downe2ja, downey2ja, noreply 
[http://corresea.com/components/com_ag_google_analytics2/test.php?html143](http://corresea.com/components/com_ag_google_analytics2/test.php?html143)

---

### Post by mr-woof on 2011-11-29
What machines do you use to log in with? Any Windows machine perhaps anywhere?

---

### Post by sdowney717 on 2011-11-29
99.9% of the time just using ubuntu box.

I do have a win7 theatre PC which I read my email on perhaps twice in 2 years. It could be I tend to use the same password on every forum I post on which is about 6 different ones.

yahoo
garage journal
ubuntu forums
cruiser forums
binder planet

are all forums I post on fairly often.

---

### Post by mr-woof on 2011-11-29
Can you still get into all those forums?

---

### Post by OrangeCrate on 2011-11-29
Though I'm sure that someone here can offer some help, you might be best served to post your problem here:

[http://www.google.com/support/forum/p/gmail?hl=en](http://www.google.com/support/forum/p/gmail?hl=en)

I assume you passed on Google's request not too long ago, that you set up the two step verification (to avoid what appears to have happened to you).

[http://www.google.com/support/accounts/bin/static.py?hl=en&page=guide.cs&guide=1056283&rd=1](http://www.google.com/support/accounts/bin/static.py?hl=en&page=guide.cs&guide=1056283&rd=1)

Live and learn, I guess. Good luck...

---

### Post by sdowney717 on 2011-11-29
all the forums I can login fine.

about the 2 step gmail login, I dont recall doing anything to setup that. At least gmail let me login and change the password using a text message sent to my phone. I dont like being tied to the cell phone to log in but I understand the benefit.

---

### Post by Dangertux on 2011-11-29
You don't by any chance have an iphone you are accessing your gmail from do you? Something similar happened to me with gmail earlier this year, I ended up tracing it back to a vulnerability in my phone.

If the answer to that is no, then it is likely you have either a weak password and/or reset questions, or you were XSS'ed in some way from a site you visited and your authentication token was stolen for gmail. Ubuntu doesn't protect against this , as it is not targeting the OS. You might wish to use NoScript if you're not currently.


Hope this helps.

---

### Post by OrangeCrate on 2011-11-29
> **sdowney717 said:**
> all the forums I can login fine.

about the 2 step gmail login, I dont recall doing anything to setup that. At least gmail let me login and change the password using a text message sent to my phone. **I dont like being tied to the cell phone to log in** but I understand the benefit.

The first time you use the new sign-in method, Google will send you, via text, a six digit authorization code that is good for 30 days. Not intrusive at all.

It's a little more complicated if you use a mail program (such as Thunderbird, as I do), but, not much.

---

### Post by shuttleworthwannabe on 2011-11-29
My account was accessed in Pakistan and later in Mexico--and I traced it to be my mobile phone (Gmail app on Blackberry)--I think it is a good idea to subscribe to 2 step authentication process and also lock your password to a device (it is a pain in the beginning, but worth the trouble, as I have a professional Gmail account with Google Apps.

Also, I have learnt to use Opera for Gmail; and I browse the web with another browser (chrome) so the login details do not propagate like above poster said--there are scripts that harvest Gmail usernames and passwrods; so be warned.

---

### Post by TheVisitors on 2011-11-29
I love Google.  It's the only site that allows me to use 50+ letters, numbers, and symbols for passwords.

I once used the following

0_+IdareYou2hackThisyouCrazysonOfa**$h-I-am-rick-_jams-$*t$ch

The day they don't allow me to use crazy things like that... Is the day I stop using them

---

### Post by coldraven on 2011-11-30
> **TheVisitors said:**
> I love Google.  It's the only site that allows me to use 50+ letters, numbers, and symbols for passwords.

I once used the following

0_+IdareYou2hackThisyouCrazysonOfa**$h-I-am-rick-_jams-$*t$ch

The day they don't allow me to use crazy things like that... Is the day I stop using them

That's not much use if it is the last item in your clipboard, any web-site can read that.

---

### Post by OrangeCrate on 2011-11-30
> **TheVisitors said:**
> I love Google.  It's the only site that allows me to use 50+ letters, numbers, and symbols for passwords.

I once used the following

**0_+IdareYou2hackThisyouCrazysonOfa**$h-I-am-rick-_jams-$*t$ch**

The day they don't allow me to use crazy things like that... Is the day I stop using them

:)

---

### Post by CryptAck on 2011-11-30
> **TheVisitors said:**
> 
0_+IdareYou2hackThisyouCrazysonOfa**$h-I-am-rick-_jams-$*t$ch


Well, there goes a possible password I could have used...

---

### Post by Erik1984 on 2011-11-30
just use correcthorsebatterystaple and you're set :P

---

### Post by TheVisitors on 2011-11-30
> **coldraven said:**
> That's not much use if it is the last item in your clipboard, any web-site can read that.

True, but who in their right mind would be crazy enough to be copying & pasting that or doing anything else which would add it into the clipboard. :P

(I'm sure some noob would though)

---

### Post by Dangertux on 2011-11-30
> **TheVisitors said:**
> True, but who in their right mind would be crazy enough to be copying & pasting that or doing anything else which would add it into the clipboard. :P

(I'm sure some noob would though)


I'm sure a lot of people would, they write them on sticky notes all the time. Also -- how many times do people do things that aren't the best idea because it "can't hurt them" quite a few.  

Examples : When was the last time you ran a browser without NoScript because Ubuntu is "Secure" or have you ever created a "secure" connection to a eCommerce site on a shared connection. Here's one that people brag about, when was the last time you clicked on one of those Windows rogueware ads because you have Linux and it can't hurt you. Those are all silly mistakes in terms of security that can really bite you.

Also the horse staple deal gives a bad impression, it's not as secure of a password as some might think, against a dictionary attack it's very secure, against methods like time memory trade off with oclhashcat (what attackers are ACTUALLY doing) it's pretty much garbage. Just a heads up ;-)

---

### Post by ivikas on 2012-05-16
Hi,

   Change your email password,secret question,recovery email address password.Never sign into or sign up to  other website using your original email address and password.

See on location bar that gmail page is from google and not from some other website.

And if your email is irrecoverable  then consult a ethical hacker to get it back.

That's all

---

### Post by Lightstar on 2012-05-16
If you use the same email and password on every website, that is likely the cause.

Not every website is secure.  I could make my own forum and invite people over while keeping their password unencrypted on my server.

---

### Post by ikt on 2012-05-16
> **sdowney717 said:**
> I am curious as to how they got the password. Earlier this year my hotmail account was also hijacked and some emails sent to those in my contact list.

Sign up to any websites that were breached? Like groker etc?

---

