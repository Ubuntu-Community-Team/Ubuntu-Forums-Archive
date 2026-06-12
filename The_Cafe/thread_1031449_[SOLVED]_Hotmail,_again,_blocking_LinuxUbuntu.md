---
title: "[SOLVED] Hotmail, again, blocking Linux/Ubuntu"
date: 2009-01-05
forum: The Cafe
---

### Post by Mark_in_Hollywood on 2009-01-05
As of January 5, 2009 at 9:24 am, my Firefox is again being blocked from Hotmail. See screenshot.

---

### Post by RiceMonster on 2009-01-05
Use gmail

---

### Post by kevin11951 on 2009-01-05
> **RiceMonster said:**
> Use gmail

you know the whole world would be happy, if there was an email service as powerful as gmail, but didn't read your email for you.  (not that im complaining ive got nothing to hide 8-[)

---

### Post by Icehuck on 2009-01-05
Gmail or Yahoo mail, better options.

---

### Post by bgs100 on 2009-01-05
> **ricemonster said:**
> use gmail

+1

---

### Post by ticopelp on 2009-01-05
> **RiceMonster said:**
> Use gmail

Wow, how amazingly helpful. 

Mark, have you tried IES4linux? [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

It's probably not optimal, but might get you into your email. You might also try to find a plugin or add-on that will let Firefox spoof itself as IE.

---

### Post by Eisenwinter on 2009-01-05
> **kevin11951 said:**
> you know the whole world would be happy, if there was an email service as powerful as gmail, but didn't read your email for you.  (not that im complaining ive got nothing to hide 8-[)
Well, if you really, **really** want something like this, the best option is hosting your own mail server, on your personal machine.

Then if you say have a 500GB disk, that's the size of your inbox, that's like almost a 100 times more than the storage size gmail offers you.

I use gmail myself, though, because I don't use my email that much anyway, and gmail is good enough.

---

### Post by eragon100 on 2009-01-05
It isn't blocked, it works fine. Just click on "Continue to windows live hotmail".

It also doesn't block linux users, because it works with opera on linux perfectly. And opera itself isn't even a supported browser.

---

### Post by 2hot6ft2 on 2009-01-05
Open Firefox and click on File>New Tab and type "about:config" without inverted commas, hit Enter then confirm that you want to access configuration.

In the filter area put general.useragent.vendor and change the value from Ubuntu to Firefox, then save and exit.

Hotmail doesn't recognize Ubuntu as a browser.

Forgot: Restart Firefox

---

### Post by littlemog on 2009-01-05
Agreed. I dled IES4linux and it was fine. Though later on Gmail got me and I never looked back. :popcorn:

> **ticopelp said:**
> Wow, how amazingly helpful. 

Mark, have you tried IES4linux? [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

It's probably not optimal, but might get you into your email. You might also try to find a plugin or add-on that will let Firefox spoof itself as IE.

---

### Post by ratmandall on 2009-01-05
I just logged in and didn't get that message.

---

### Post by kelvin spratt on 2009-01-05
That message does not appear using Ffox 3.05  or Swiftfox 3.04 on my machines.

---

### Post by chamber on 2009-01-05
Works fine for me.

---

### Post by Ptero-4 on 2009-01-05
> **kevin11951 said:**
> you know the whole world would be happy, if there was an email service as powerful as gmail, but didn't read your email for you.  (not that im complaining ive got nothing to hide 8-[)
Actually, every email provider opens email messages before delivering (required for proper funcioning of most spam filters). Google is just being more honest about this fact, and they were the only ones who stood up and gave the gov. the double deuce when the gov. came flinging the patriot act and forcing search and email providers to disclose their result lists and email messages.

---

### Post by 2hot6ft2 on 2009-01-05
And here's the long version.
> **2hot6ft2 said:**
> Found 3 possible solutions and tried all 3 plus a a little checking and finally got it working again. Since I've been pasting the fixes in a txt file I'll break them down.

To fix live hotmail in firefox I did both of these

1. In the address bar of Firefox put about:config hit enter, in the Find put general.useragent.vendor Select it and Right click on it then select Modify and change it to Firefox from Ubuntu, then restart Firefox.

2. In Firefox click on Tools then Add-Ons > Get Add Ons and put User Agent Switcher in the search and install it then follow the instructions in the quote below.

BEGIN QUOTE-----------------------
Install the User Agent and create a profile: (if you are using Firefox 3.x on Linux)

Descriptiong: Firefox 3.x (WinXP)
User Agent: Mozilla/5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
App name: Mozilla Firefox
App Version: 5.0 (Windows; U; Windows NT 5.1; en-US; rv:1.9.0.3) Gecko/2008092417 Firefox/3.0.3
Platform: Win32
Vendor: {leave blank}
Vendor Sub: {leave blank}

and you'll be able to use the new Live Hotmail just fine! You'll even skip the dialog page that ask you to upgrade to IE, FireFox, etc..

I think this proves that Microsoft has intentionally gone out of their way AGAIN! need I say more?

--Doug

P.S.> if you are using Firefox 2.x on Linux:
Description: Firefox 2.x (Win2K)
User Agent: Mozilla/5.0 (Windows; U; Windows NT 5.0; en-US; rv:1.8.1.17) Gecko/20080829 Firefox/2.0.0.17
App Name: Mozilla Firefox
App version: 5.0 (Windows; U; Windows NT 5.0; en-US; rv:1.8.1.17) Gecko/20080829 Firefox/2.0.0.17
Platform: Win32

and if you are sick, go ahead and lie to Live Hotmail on a Windows machine using Firefox 2.x/3.x but claim you are on Linux .. and you'll be unable to use Live Hotmail correctly!

change the Platform to Linux and the Agent to "Mozzila/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.17) Gecko/20080922 Ubuntu/7.10 (gutsy) Firefox/2.0.0.17" (and app version to the "5.0 (X11 ..." part) and Platform to Linux!

(or equiv for Firefox 3.x which I won't bother to post)
dx9ss
END QUOTE-----------------

When I did this and went to hotmail to send a test email I could compose it but it wouldn't send it UNTIL I clicked on Tools > User Agent Switcher and selected the Firefox 3.x (WinXP) profile I had created. Once I did it sent it on its way.

****************************
Firefox fixed:D Now for Thunderbird
***************************

1. In Thunderbird Open Tools Add-ons dialog ->Webmail-Hotmail -> Preferences -> Change mode to WebDav. Restart Thunderbird

2. Check all your setting for ports and SMTP servers i.e.
Open Tools Add-ons dialog ->Webmail >Preferences and make sure the ports are still set.

3 Go thru your accounts settings and make sure both the ports AND the SMTP servers are set right (mine had changed):confused: I also had to change my SMTP to my email address ########@hotmail.com Once everything is as it should be restart Thunderbird and cross your fingers.

If it still doesn't work go back thru and check it again maybe you overlooked something. Good luck

P.S. I did NOT uninstall and reinstall my Webmail or Hotmail plugins in Thunderbird.

Hope this helps.:guitar:

---

