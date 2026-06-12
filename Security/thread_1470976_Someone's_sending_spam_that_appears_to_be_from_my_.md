---
title: "Someone's sending spam that appears to be from my Hotmail account"
date: 2010-05-03
forum: Security
---

### Post by oscar615 on 2010-05-03
After reading everything that says you don't need an anti-virus for Linux.  OR Linux doesn't get viruses.  Guess what I have a Virus.

I don't know which one, but it is sending out spam emails from my webmail, MSN, account.  I do not have a local client installed.  I am guessing it is linking into MSN through Pidgin, getting the addresses there, and sending the spam, somehow, through MSN.  Actually one MSN and one Hotmail account.

I also have not been able to find an anti-virus program for Ubuntu.  There do not seem to be any listed in the software repositories that Ubuntu links into.

So my question is, how do I get rid of it?  My contacts are starting to get upset.

Thanks for any help.

---

### Post by varunendra on 2010-05-03
Are you sure your mail accounts aren't compromised & it's your Linux OS for sure?
Can you provide details of the spam mails? (Their contents, the links they contain, etc.)

Depending upon the frequency of these outgoing "spam" mails, I'd suggest to use a different setup or entirely a different OS to logon to your accounts & see if this "spamming" stops.
If it doesn't, then your accounts have been compromised (or misused by some website to which u might have registered giving out your account details in the past)

I've faced such problem some days ago & immediately changing my account details, password, alternate mail ID & security options, etc. solved the problem.

As for antivirus solution, you can try clamav. It is one of the best & is included in repositories. It is not "on-access" scanner though, that means you'll have to manually start the scanning for viruses. You may like to add a gui frontend to it (like clamtk)

---

### Post by CharlesA on 2010-05-03
Change yer email password and whatnot. I doubt that Ubuntu caused it to become compromised.

If you had a weak password to begin with, that was more then likely the cause.

---

### Post by EJeanmaire on 2010-05-03
> **oscar615 said:**
> After reading everything that says you don't need an anti-virus for Linux.  OR Linux doesn't get viruses.  Guess what I have a Virus.

I don't know which one, but it is sending out spam emails from my webmail, MSN, account.  I do not have a local client installed.  I am guessing it is linking into MSN through Pidgin, getting the addresses there, and sending the spam, somehow, through MSN.  Actually one MSN and one Hotmail account.

I also have not been able to find an anti-virus program for Ubuntu.  There do not seem to be any listed in the software repositories that Ubuntu links into.

So my question is, how do I get rid of it?  My contacts are starting to get upset.

Thanks for any help.

I don't think that you have a virus on your Ubuntu install.  There are much more likely scenarios, such as:

1.  You had your account information stolen through social engineering (fake websites requiring your Windows Live or MSN ID).

2.  You have MSN and hotmail, so I am 99% will to bet that you have a Windows installation, or had one.  Perhaps that installation was compromised?  

3.  You logged into Hotmail, MSN from a non-trusted computer.

Do any of these apply?

---

### Post by oscar615 on 2010-05-03
The only way I knew that it was sending them is I started to get the emails bouncing back to me.  here are some of the links it was sending out from the hotmail account.
[noparse]http://jonnyb2745.solidwebhost.com/
http://philomenau8632.freehostwebs.com/
http://tannau4564.100gbfreehost.com/
http://bonniei6080.justfree.com/
http://reniem5696.freehostwebs.com/[/noparse]

and from the msn account
[noparse]http://tannau4564.100gbfreehost.com/[/noparse]

No text in the emails.  Just a link.

And the subject in all of them is, RE:

I used to use windows.  and my Linux box is actually a dual boot machine.  But I don't really use windows anymore.  Just toooooo  slow.  I do have another windows machine on the network.  I will look into that but it usually is not booted up.  I don;t think I logged into my email from a windows machine for a long time.

It seems weird that two of my email accounts would have been compromised on the same day.

I was thinking Linux because it is pretty much the only machine I use and is always turned on.

---

### Post by EJeanmaire on 2010-05-03
> **oscar615 said:**
> The only way I knew that it was sending them is I started to get the emails bouncing back to me.  here are some of the links it was sending out from the hotmail account.
[noparse]http://jonnyb2745.solidwebhost.com/
http://philomenau8632.freehostwebs.com/
http://tannau4564.100gbfreehost.com/
http://bonniei6080.justfree.com/
http://reniem5696.freehostwebs.com/[/noparse]

and from the msn account
[noparse]http://tannau4564.100gbfreehost.com/[/noparse]

No text in the emails.  Just a link.

And the subject in all of them is, RE:

It seems weird that two of my email accounts would have been compromised on the same day.

How did you determine that your account sent these?

---

### Post by sydbat on 2010-05-03
The question no one has asked yet - when you check your email, do you go to the MSN site and check online? Or do you use a mail client like Thundrbird and download all your emails from the MSN server AND leave a copy of the emails on the MSN server.

I guess it doesn't matter because it sounds like the MSN server is the place that is compromised. Not surprising.

---

### Post by oscar615 on 2010-05-03
First, I received emails from friends telling me I was sending spam and second, I started receiving some that had bounced back to me because the addresses they were sent to are no longer valid.

I log into webmail.  I do not use a local email client, yet.

I am going to change the passwords and see if that helps.

---

### Post by lovinglinux on 2010-05-03
It is probably just a spammer using your address without even passing through MSN servers or your computer. I don't think changing your password will stop them, but is definitely a good idea to change it.

---

### Post by aysiu on 2010-05-03
I've retitled the thread to more appropriately reflect what's happening. In a support thread, it's better to describe the symptoms than your own conclusions about what the cause of the problem is.

As others have pointed out, it's possible someone may have compromised your account if you have a weak password. It's also possible (in fact, probable) your account isn't compromised at all but that someone is merely spoofing your email address and sending email that appears to be from you but isn't even coming through the Hotmail servers.

P.S. Even if some malware had compromised your Ubuntu installation, placebo "antivirus" would not have stopped it.

---

### Post by cariboo on 2010-05-03
I have had the same sort of problem, with an email address that was available all over the place, the spammer usually doesn't actually use your account to sent the email, they just spoof your email address, the best way to see if the email is actually coming from your account is to check the headers. 

```
Message-ID: <4ACD291A.1050603@shaw.ca>
Date: Wed, 07 Oct 2009 16:49:46 -0700
From: me <my_email_address@shaw.ca>
User-Agent: Thunderbird 2.0.0.23 (X11/20090817)
MIME-Version: 1.0
To: Kie Chow <kiec.bc@daiwa.net>
Subject: Re: Daiwa -Kie
References: <F372FE327DE54D4397BF543CC081AC72@DAIWA>
In-Reply-To: <F372FE327DE54D4397BF543CC081AC72@DAIWA>
Content-Type: text/plain; charset=windows-1252; format=flowed
Content-Transfer-Encoding: 8bit
```

The header should look something like the above example. I've removed my name and email address. The person I sent the email to no longer works for that company.

---

### Post by DrMelon on 2010-05-03
Change your password immediately - someone has control of your account. This is not OS-side thing, it is not a virus, someone has guessed or dictionary-cracked your email password. Change it ASAP.

---

### Post by sakisds on 2010-05-03
Exactly as aysiu said, someone can easily spoof emails so it seems like you sended them. If you change the password and the emails still go out, that can be the case.

---

### Post by OpSecShellshock on 2010-05-03
I'm leaning a little more toward compromised account than spoofed address in this case only because the recipients seem to be in the thread starter's stored contacts. One thing you may want to do after the passwords have been changed is check to see if there's a signature appending itself to outgoing messages. Happened to someone I knew. Careful, too. When I checked that account it looked like the signature area was blank, but when I selected everything inside the text entry field there was something there, which I deleted--and that solved the problem.

Something I've noticed when friends send me messages from hotmail or live or msn accounts is that there are advertisements for the service appended to all of the messages. I suppose it's possible that whoever cracked the account also knew how to manipulate that content.

---

### Post by Jive Turkey on 2010-05-03
Based on the limited information here is seems your account(s) is(are) compromised and not just being spoofed.  I think so because the these emails are being sent to your contacts, and not just random people.  They would need to have access to your account to get the contacts, or at least they should, msn might publish your contacts somewhere, I don't know.

There are some pretty sophisticated systems out there for brute force guessing of passwords out there.  You should make sure you have strong passwords on everything, and different ones for different services.  Change them regularly as well.

---

### Post by olive.ewe on 2010-05-03
I know a while back there was (and may still be) an extension for thunderbird that  showed the original source of an email and the send route, even the mail client/software used to send the email, but I cannot remember the name.(assuming of course that your email address is being spoofed). You can have a look at  [https://addons.mozilla.org/en-US/thunderbird/](https://addons.mozilla.org/en-US/thunderbird/)

---

### Post by CharlesA on 2010-05-03
I have thunderbird set to display the full headers. If you scroll down to "mailed by" I'll tell you the domain it was mailed by.

---

### Post by noway2 on 2010-05-03
To get the message headers from Hotmail, right click on the email and select message source (bottom of the list).  Thought I would post that tip because it is a little less than obvious how to get that info in hotmail.

---

