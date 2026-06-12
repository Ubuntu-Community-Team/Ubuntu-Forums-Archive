---
title: "Adware problem"
date: 2010-10-08
forum: Security
---

### Post by Lemuel111 on 2010-10-08
I use Ubuntu 10.04 but my dad uses Windows and last night he rang me to say that he had received 3 emails off me containing spyware after doing a spyware check on his system. The 3 are:-
1. Adtech
2. Adviva
3. Apmebf
All cookies. I did a search on my system including external hard drive and could only find adtech which was in documents & settings. I have deleted then emptied those files out of the wastebasket. Is there a linux spyware programme I can use to find the other ones? I wonder have they come from searches on the net or stuff I transfred over from the days of Windows? How do I stop this happening in the future?

---

### Post by OpSecShellshock on 2010-10-08
> **Lemuel111 said:**
> I use Ubuntu 10.04 but my dad uses Windows and last night he rang me to say that he had received 3 emails off me containing spyware after doing a spyware check on his system. The 3 are:-
1. Adtech
2. Adviva
3. Apmebf
All cookies. I did a search on my system including external hard drive and could only find adtech which was in documents & settings. I have deleted then emptied those files out of the wastebasket. Is there a linux spyware programme I can use to find the other ones? I wonder have they come from searches on the net or stuff I transfred over from the days of Windows? How do I stop this happening in the future?

It seems to me that these are most likely remnants from the old Windows installation. Documents & Settings is a Windows-specific directory (however, whatever was contained in there probably wouldn't run on Linux anyway). Another option is that if you use one of the free webmail providers, that your account has been compromised in some way. Changing the password for that service is probably a good idea.

You should be able to configure your email settings so that you only compose messages in plain text. Your father might also be able to configure his so that he only receives them in plain text. This can help to avoid the rendering of html and active scripting within the body of an email message. At times it's really not pretty to look at with all the broken images and tags everywhere, but at least it's not loading anything malicious.

---

### Post by P4man on 2010-10-08
What the above poster said: your mail account is most likely compromised, and some bot is using it to send infected spam. Change your email password asap. 

Malware for ubuntu is not impossible in theory but extremely rare.

---

### Post by Lemuel111 on 2010-10-08
Which mail would it be my hotmail which I go in through the net or my googlemail which comes via Evolution?

Thanks.

---

### Post by P4man on 2010-10-08
which ever account your father received infected mails from. But if one account was compromised by a malware password stealer, then you should really change both passwords. Or rather, change ALL your passwords. Email, facebook, banking account, ebay, whatever.

---

### Post by Lemuel111 on 2010-10-08
Thanks. I have removed Documents & Settings from both drives but is there some linux software which I can check that I have got rid of the adware?

---

### Post by P4man on 2010-10-08
im not quite sure you understand. If our assumptions are correct, then you have had a malware infection on windows, some mailicious code that harvested your accounts and account passwords, for email, facebook  and whatever else you use. Those are now being used by bots to send spam or more malware from your email accounts hosted at hotmail, gmail facebook or whatever,  to your contacts. You can burn your PC in an incinerator and it wont solve the problem, if your accounts are compromised.

Deleting documents and settings serves no purpose really; that malware wouldnt work on ubuntu, but the damage is already done. Fix it by changing all your passwords on any webservice you use. Paypal comes to mind too. eBay. Heck, this forum.

---

### Post by Lemuel111 on 2010-10-08
O I see! Will the password change need to the password used to update manager etc? But once I've changed the passwords will there not be a potential for it to happen again as the advent cookie was on my system?

---

### Post by Lemuel111 on 2010-10-08
Sorry I meant AdTech not advent!

---

### Post by P4man on 2010-10-08
Im not talking about your ubuntu password. Im talking about your gmail login+password. Hotmail password. Facebook password. Paypal password. These services can be accessed from any PC by any user or a bot if they have your login and passwords. They dont need your PC anymore.

And no, cookies are no problem

---

### Post by Lemuel111 on 2010-10-08
No I realise that it's all passwords web based but just worried that once I've changed the same problem will occur in future.

---

### Post by slooksterpsv on 2010-10-08
It very well could, just exercise caution, as for scanning for malware on a Windows partition in Linux, try ClamAV (not my favorite), Avira (great detection rates, can be confusing to get started), or AVG (Difficult to get GUI up)

---

### Post by lisati on 2010-10-08
Another possibility is that a spammer has either guessed your email address or discovered it somewhere online and forged your email address in the "from" header.

Have a look here: [http://en.wikipedia.org/wiki/E-mail_spoofing](http://en.wikipedia.org/wiki/E-mail_spoofing)

---

### Post by The Cog on 2010-10-08
Bear in mind that if he got your email account, he can possibly use the password reset facility on any number of other web sites that you have accounts on, and use your mail account to confirm the password resets. This happened to a friend of mine yesterday.

---

### Post by SeijiSensei on 2010-10-08
I maintain some closed-subscription listservers and have seen two cases recently where spams were sent from legitimate accounts on Hotmail.  The messages originated on Hotmail's own servers so they weren't forged. It may be that someone has stolen your credentials and is sending spam from your account.

If your father still has the messages, see if you can have him view the entire message source with all the headers.  In Thunderbird this is simply a matter of using Edit > View Source, but other mail clients like Outlook make it much more difficult.  ([This article](http://kb.mediatemple.net/questions/893/How+to+View+Email+Headers) appears to provide an extensive list of techniques for a number of email clients.) Without being able to see the full headers it's impossible to determine whether your email address is being forged on messages sent from a third-party mail server, or whether your account is compromised.

In the headers he'll see a number of lines that begin "Received".  These track the route of message as it wends its away though one or more  SMTP servers.  One of the last of these should identify the server that sent the message to the server that handles your father's account.  If that's a legitimate server in hotmail.com or gmail.com, you've been compromised.

---

### Post by Lemuel111 on 2010-10-08
**Re: Adware problem**
 		"I maintain some closed-subscription listservers and have seen two  cases recently where spams were sent from legitimate accounts on  Hotmail.  The messages originated on Hotmail's own servers so they  weren't forged. It may be that someone has stolen your credentials and  is sending spam from your account.

If your father still has the messages, see if you can have him view the  entire message source with all the headers.  In Thunderbird this is  simply a matter of using Edit > View Source, but other mail clients  like Outlook make it much more difficult.  ([This article]("http://kb.mediatemple.net/questions/893/How+to+View+Email+Headers")  appears to provide an extensive list of techniques for a number of  email clients.) Without being able to see the full headers it's  impossible to determine whether your email address is being forged on  messages sent from a third-party mail server, or whether your account is  compromised.

In the headers he'll see a number of lines that begin "Received".  These  track the route of message as it wends its away though one or more   SMTP servers.  One of the last of these should identify the server that  sent the message to the server that handles your father's account.  If  that's a legitimate server in hotmail.com or gmail.com, you've been  compromised. 	"

.................................................................................................................................

My dad will have cleared my emails off via is virus software programme by now, so not much hope there. All the above just makes me more unsure that just by changing my password can't guarantee the same company/individual won't be able to do the same again. 
Should I also use a different web browser than firefox which I thought was supposed to be reasonably safe?

---

### Post by P4man on 2010-10-09
Its usually not the browser that causes someone to steal your identities. Its usually malware you download and install from some place. A tool, a plugin, a screensaver a "free virus scanner", a cool email icon set, a warez site "download accelerator". You can do that with any browser. You can also do that with any OS, but there is nearly no malware that actually works on ubuntu, its almost all windows.

Stay away from windows, enable the common sense switch in your head and you should be okay (after you changed all your passwords).

---

### Post by BigCityCat on 2010-10-09
If your still using windows it's also possible that it is compromised and even if you change your passwords they could be stolen again. I'm not saying it happened like that. They could have just hacked your account because of a weak password. 

I would install malwarebytes and superantimalware on your windows system and scan with them. My problem with windows is you can never be sure. If there is something there and it's new then it won't be in the virus database of any program. They create new stuff so fast that the virus companies can't keep up. They are in a perpetual state of catch up. If your compromised in windows then I would just re install windows and then to be safe...don't use it unless you have to.

None the less do what everyone said. Change all your passwords using Linux. Of course I am assuming you are still using windows in some capacity.

---

### Post by Lemuel111 on 2010-10-10
No I don't use Windows any more apart from if using my wife's laptop (can't convince her to make the switch unfortunately!). I just transferred most of my stuff off my old computer into Ubunutu, which includes Windows files. My desktop and laptop are Ubuntu which I am generally quite happy with. I notice the Ubuntu handbook suggests that it is probably best to get virus software for Ubunutu despite the fact the majority of virus' are written for Windows as more & more stuff will start to affect Linux. Does ClamTK include getting rid of malware for future reference?

---

### Post by ehode on 2010-10-11
I think what you are missing is that it is most likely your hotmail account is compromised via either phishing or sniffed or forced.

Do you ever check hotmail on your wife's laptop?

Do you ever check hotmail at a public computer?

Do you register on forums or places when they ask for a email address you provide your @hotmail.com and when they ask for a password you use the same password?  

I am seeing a lot of compromised hotmail, gmail and yahoo accounts and I've never found a lick of malware on the system.  This goes for Windows folks and Macintosh folks.

A keylogger could be a possibility but it would be really remote chance.  If you feel you cannot trust your systems, then hey maybe this is a perfect time to clean install 10.10.

---

### Post by seeker5528 on 2010-10-11
> **Lemuel111 said:**
> I use Ubuntu 10.04 but my dad uses Windows and last night he rang me to say that he had received 3 emails off me containing spyware after doing a spyware check on his system. The 3 are:-
1. Adtech
2. Adviva
3. Apmebf
All cookies.

If these were all that were found, what is the reasoning for thinking these were "in the email you sent"?

I can't say I've ever got a cookie in my email, how would this work?

If you sent some html *and* that html pulls content from the web, then the server could have sent a cookie, but that cookie would not be "in the email".

Images, videos, etc... could also have embedded urls in them that cause a web site to be displayed when these are viewed inline.

> **OpSecShellshock said:**
> You should be able to configure your email settings so that you only compose messages in plain text. Your father might also be able to configure his so that he only receives them in plain text. This can help to avoid the rendering of html and active scripting within the body of an email message.

Depending on what you are using to read the email, there may be better options than that. Not usually things that I am looking for, but Outlook Express for example has an option to display html, but not to display anything from the web, which to me is the best security versus function balance.

Later, Seeker

---

