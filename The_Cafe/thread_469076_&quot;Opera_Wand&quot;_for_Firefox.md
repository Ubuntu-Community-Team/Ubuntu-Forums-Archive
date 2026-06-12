---
title: "&quot;Opera Wand&quot; for Firefox"
date: 2007-06-09
forum: The Cafe
---

### Post by RAV TUX on 2007-06-09
If you like the Opera Wand you'll love "Secure Login"

[IMG]https://addons.mozilla.org/en-US/firefox/images/addon_preview/4429/1[/IMG]

Secure Login version 0.8.1.2, released on Jun 09, 2007 
[https://blueimp.net/mozilla/Secure%20Login/]("https://blueimp.net/mozilla/Secure%20Login/")

Secure Login 0.8.1.1                                     
[https://addons.mozilla.org/en-US/firefox/addon/4429](https://addons.mozilla.org/en-US/firefox/addon/4429)


> 
                                         [IMG]https://addons.mozilla.org/en-US/firefox/images/addon_icon/4429[/IMG]             
                              **Secure Login 0.8.1.1                                     [[IMG]https://addons.mozilla.org/img/developers/homepage_small.png[/IMG]]("https://blueimp.net/mozilla/")                                 **

                  by                [Sebastian Tschan]("https://addons.mozilla.org/en-US/firefox/user/100849")              
         
             A login extension similar to Opera's Wand login.
         
                               It uses the built-in password manager, but deactivates the prefilling of login forms.
Instead, you are now able to login with one click or a keyboard shortcut (ALT+N - changeable via settings).
Just add the Secure Login toolbar button to your toolbar, or use the provided statusbar icon.

If you hover over one of the icons, a tooltip is shown, displaying the login url and the number of available logins (users).
For more than one user or login forms on the current page a selection prompt is displayed on login.
You have the option to play sound notifications (*.wav) for found login data on the current page or when logging in.
All the options can be changed using the Secure Login settings page. The settings page can be opened via the Secure Login tools menu, the Secure Login statusbar icon context menu or via the list of installed extensions.

Secure Login provides you with a number of Security enhancements and helps protecting you from phishing:

Disabling the prefilling of login forms prevents malicious JavaScript code to automatically steal your login data.
This is due to the fact that no login data is inserted in form fields before the user clicks on the login button or logs in using the keyboard shortcut.
To make sure you login to the right website, the second level domain of the login url is compared to the second level domain of the current page.
If they do not match a dialog prompt is displayed before login.

Secure Login provides you with an optional setting to protect you from all JavaScript code during login.
This can prevent cross-site scripting (XSS) attacks without having to deactivate JavaScript completely.
If you enable this option, your login data will never be inserted in any form fields nor will the login form be submitted.
Instead your credentials will be sent to the login page using internal Firefox methods.
Not all login forms will work this way, e.g. not those using JavaScript routines. Therefore, you can add such websites to an exception list.
         
                           Works with:[LIST]
[*]             [IMG]https://addons.mozilla.org/img/app-icons/firefox_small.png[/IMG]            Firefox:             1.5 &#8211; 3.0a5[/LIST]

---

### Post by kerry_s on 2007-06-09
Sweet! But i'm moving away from firefox to opera, cause opera just perfoms better on my 450mhz 256ram setup. Bummer :(

---

### Post by RAV TUX on 2007-06-09
> **kerry_s said:**
> Sweet! But i'm moving away from firefox to opera, cause opera just perfoms better on my 450mhz 256ram setup. Bummer :(
I still use them both, like you I prefer Opera over Firefox, it is simply more reliable and faster.

---

### Post by hummingbird59 on 2007-06-09
Thank you for the post Rav Tux!  I am a huge opera fan but I find it is slow....on my machine with Linux (tried a bunch of fixes nothing yet but that's another story) so I use Firefox.  Nothing wrong with Firefox used it for many years but Opera is so fast.....Anyway, this add-on will help me miss opera a little less :)!

---

### Post by starcraft.man on 2007-06-09
Hmmm, I dunno... I already got like 25 extensions I think... if I add one more Firefox might just implode and suck my computer in with it :p.

I will have a look at it later :).

---

### Post by RAV TUX on 2007-06-09
> **hummingbird59 said:**
> Thank you for the post Rav Tux!  I am a huge opera fan but I find it is slow....on my machine with Linux (tried a bunch of fixes nothing yet but that's another story) so I use Firefox.  Nothing wrong with Firefox used it for many years but Opera is so fast.....Anyway, this add-on will help me miss opera a little less :)!
good welcome

---

### Post by madblueimp on 2007-07-02
Thanks for suggesting Secure Login to the Ubuntu Community, RAV TUX.

I'm developing [Secure Login]("https://blueimp.net/mozilla/Secure Login/") and [Autofill Forms]("https://blueimp.net/mozilla/Autofill Forms/") on Xubuntu Linux. :)

Greetings, Sebastian

---

### Post by RAV TUX on 2007-07-02
> **madblueimp said:**
> Thanks for suggesting Secure Login to the Ubuntu Community, RAV TUX.

I'm developing [Secure Login]("https://blueimp.net/mozilla/Secure%20Login/") and [Autofill Forms]("https://blueimp.net/mozilla/Autofill%20Forms/") on Xubuntu Linux. :)

Greetings, Sebastian

Sebastian

Wow, thats pretty cool....Good Welcome.

I would like to include more articles about Open Source projects like yours on [Distropedia]("http://distropedia.com/").

I am pretty busy your welcome to join up and add your project; create a static "page", then a "Book Page" with a link to your static page. ;)

Look forward to seeing you on Distropedia.

Jozef

---

### Post by kerry_s on 2007-07-02
secure login is great, i just wish it had a option to select remember. as it is now we don't know which website blocks the saving of auto logins until after the first try, then we got to back out to do it again using the remember password bookmarklet to by pass. still other than that it's great, it's 1 of the few icons i keep in my bar. :p

---

### Post by madblueimp on 2007-07-04
> **RAV TUX said:**
> Sebastian

Wow, thats pretty cool....Good Welcome.

I would like to include more articles about Open Source projects like yours on [Distropedia]("http://distropedia.com/").

I am pretty busy your welcome to join up and add your project; create a static "page", then a "Book Page" with a link to your static page. ;)

Look forward to seeing you on Distropedia.

Jozef
Thanks for the welcome. :)
Distropedia sounds like an interesting project - but keeping my own pages and my extensions on addons.mozilla.org up to date already takes too much time so I'm not eager to edit any wiki pages at the time being.


> **kerry_s said:**
> secure login is great, i just wish it had a option to select remember. as it is now we don't know which website blocks the saving of auto logins until after the first try, then we got to back out to do it again using the remember password bookmarklet to by pass. still other than that it's great, it's 1 of the few icons i keep in my bar. :p
Hmm, applying the "remember password" code to every page would be a drawback on performance - that's the reason it's not included in Secure Login.


**If you have any suggestions or support requests, please post on the [mozillazine forums]("http://forums.mozillazine.org/viewtopic.php?t=515894"). This way, I can help out users not using Ubuntu as well. :)**

---

