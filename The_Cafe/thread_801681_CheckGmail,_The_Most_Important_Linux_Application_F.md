---
title: "CheckGmail, The Most Important Linux Application For Me. Revie Included"
date: 2008-05-20
forum: The Cafe
---

### Post by hotweiss on 2008-05-20
The application that I miss the most after leaving Linux for any short period of time is CheckGmail. That is why I have put in the time to write a detailed review about it. Tell me what you guys and gals think.

[http://seethisnowreadthis.com/2008/05/20/checkgmail-linuxs-blackberry/](http://seethisnowreadthis.com/2008/05/20/checkgmail-linuxs-blackberry/)

For me, it's the most useful application on the Linux platform. Please Digg it if you like it:

[http://digg.com/linux_unix/CheckGmail_Linux_s_Blackberry](http://digg.com/linux_unix/CheckGmail_Linux_s_Blackberry)

Likewise, bump it on reddit.com:

[http://reddit.com/info/6k5vi/comments/](http://reddit.com/info/6k5vi/comments/)

---

### Post by Praxicoide on 2008-05-21
Nice article.

One thing though, are you sure about the last package "libcrypt-perl-simple"? I couldn't find it anywhere.

EDIT: it's libcrypt-simple-perl. You might want to change that

---

### Post by hotweiss on 2008-05-22
> **Praxicoide said:**
> Nice article.

One thing though, are you sure about the last package "libcrypt-perl-simple"? I couldn't find it anywhere.

EDIT: it's libcrypt-simple-perl. You might want to change that

Thanks. Didn't notice my mistake.

---

### Post by meborc on 2008-05-22
nice article... i have used checkgmail before, but i never new about the opening mail not in browser, but in the window thing...

there is one thing though... you have a command:
[B]
sudo perl -MCPAN -e &#8216;install Gtk2::Sexy&#8217;[/B]

which should be

[B]
sudo perl -MCPAN -e 'install Gtk2::Sexy'[/B]

see the difference is in the " ' " marks ;)

(edit: it really doesn't show here, but i got an error when copy/pasting from your article)

oh, and doing all this >    1. Intsall the Perl ExtUtils Dependencies by typing the following in Terminal:
      sudo apt-get install libextutils-depends-perl libextutils-pkgconfig-perl
   2. Install the libsexy dependency by typing the following in Terminal:
      sudo apt-get install libsexy2 libsexy-dev
   3. Now you have to install Gtk2-Sexy by typing the following in Terminal:
      sudo perl -MCPAN -e &#8216;install Gtk2::Sexy&#8217;
      If you get an error during this step, it&#8217;s because you haven&#8217;t configured cpan. Type cpan in the Terminal window and just keep on pressing enter until you have completed the installation.
   4. You are almost there, now install the dependency that is required for the encryption of your password by typing the following in Terminal:
      sudo apt-get install libcrypt-simple-perl
   5. Reboot for the changes to take into effect.

still doesn't allow me to view the mail anywhere else then in browser :(

(edit2: ok, got it... instead of open, i must click on the title... )

:)

---

### Post by hotweiss on 2008-05-22
> **meborc said:**
> nice article... i have used checkgmail before, but i never new about the opening mail not in browser, but in the window thing...

there is one thing though... you have a command:
[B]
sudo perl -MCPAN -e ‘install Gtk2::Sexy’[/B]

which should be

[B]
sudo perl -MCPAN -e 'install Gtk2::Sexy'[/B]

see the difference is in the " ' " marks ;)

(edit: it really doesn't show here, but i got an error when copy/pasting from your article)

oh, and doing all this 
still doesn't allow me to view the mail anywhere else then in browser :(

(edit2: ok, got it... instead of open, i must click on the title... )

:)

I will make the appropriate changes in the write-up. Thanks again.

---

### Post by tdrusk on 2008-05-22
Can you post a screenshot of it being open in a window rather than a web browser?

---

### Post by hotweiss on 2008-05-22
[http://img443.imageshack.us/img443/2555/screenshotbd4.0605062477.jpg](http://img443.imageshack.us/img443/2555/screenshotbd4.0605062477.jpg)

---

### Post by damis648 on 2008-05-22
hmm i check my gmail with evolution but i like this... i might try it out.

---

### Post by enchantedsky on 2008-05-22
What's so special about this program? There have been tons of Firefox extensions which automatically check your gmail for you. How often do you have Firefox closed, in which you really need it to alert you that you email?

---

### Post by LaRoza on 2008-05-22
> **enchantedsky said:**
> What's so special about this program? There have been tons of Firefox extensions which automatically check your gmail for you. How often do you have Firefox closed, in which you really need it to alert you that you email?

Perhaps it is lighter? Firefox isn't the lightest thing, especially with its extensions.

(Oh, Opera has this feature out of the box and it is light)

---

### Post by hotweiss on 2008-05-22
> **enchantedsky said:**
> What's so special about this program? There have been tons of Firefox extensions which automatically check your gmail for you. How often do you have Firefox closed, in which you really need it to alert you that you email?

Try it out. It is really convenient, you'll hate opening your browser to check your email after a while.

---

### Post by pt123 on 2008-05-22
Pity it can't remeber the password using gnome keyring like cgmail

---

### Post by meborc on 2008-05-23
i like the way it is possible to set your numlock light to blink... it is very useful when you are expecting an important mail, but you are playing a fullscreen game...

you will notice the light blinking instantly... very cool!!!

---

### Post by karellen on 2008-05-23
I suppose it's useful, anyway I use Evolution for checking my gmail account, it's more convenient for various tasks

---

### Post by tdrusk on 2008-05-23
Just to put in how I feel, I love this program. It notifies me off all the messages I receive and I set my social networking sites to send me an email when something happens. That way I don't have to keep checking them, checkgmail just tells me.

---

### Post by olskar on 2008-05-23
Anyone knows why it takes so long to open this program in hardy? And CPU is at 100%..

---

### Post by hotweiss on 2008-05-23
> **olskar said:**
> Anyone knows why it takes so long to open this program in hardy? And CPU is at 100%..

Yes, I noticed that to. That freeze started to occur as of version 1.13. I really don't see it as an issue as there only is a pause for 3 seconds and then the application launches with no problems to follow.

---

### Post by Stefanie on 2008-05-23
i followed the steps, but i still can't open new mails in the checkgmail window... when i click on the title i only see the first 2 lines.

---

### Post by tdrusk on 2008-05-23
> **hotweiss said:**
> Yes, I noticed that to. That freeze started to occur as of version 1.13. I really don't see it as an issue as there only is a pause for 3 seconds and then the application launches with no problems to follow.

Hmm. I guess I have never noticed that since I have it set to start at boot.

---

### Post by Stefanie on 2008-05-23
> **Stefanie said:**
> i followed the steps, but i still can't open new mails in the checkgmail window... when i click on the title i only see the first 2 lines.

problem solved by upgrading from 1.12 to 1.13... maybe this is useful to include in the howto.

---

### Post by hotweiss on 2008-05-23
> **Stefanie said:**
> problem solved by upgrading from 1.12 to 1.13... maybe this is useful to include in the howto.

If you follow my instructions, you should download 1.13. How did you manage to download 1.12?

---

### Post by Stefanie on 2008-05-23
> **hotweiss said:**
> If you follow my instructions, you should download 1.13. How did you manage to download 1.12?

i  was using checkgmail already (downloaded it from the repos a month ago), but i didn't know about this "show entire message" function. you didn't mention that it doesn't work below 1.13, so i really wasn't aware of potential problems with 1.12. i even didn't know i didn't have the latest version. i just followed your instructions, it wasn't working so after trying a few things i figured the problem was due to an outdated version. (i still wonder why 1.13 is not in the repos yet). 
so i'd suggest you remind people to check if they have 1.13 and not 1.12.

---

### Post by hotweiss on 2008-05-23
> **Stefanie said:**
> i  was using checkgmail already (downloaded it from the repos a month ago), but i didn't know about this "show entire message" function. you didn't mention that it doesn't work below 1.13, so i really wasn't aware of potential problems with 1.12. i even didn't know i didn't have the latest version. i just followed your instructions, it wasn't working so after trying a few things i figured the problem was due to an outdated version. (i still wonder why 1.13 is not in the repos yet). 
so i'd suggest you remind people to check if they have 1.13 and not 1.12.

Got it. Thanks for clearing that up. That's strange, as with 1.12 you were able to view the messages within the pop-up also.

I've also have broken down the install into a few steps, making it easier to look at.

---

### Post by pt123 on 2009-10-13
anyone else having troubles logging in with this application and have to resort to running it:
checkgmail -no_cookies

---

### Post by subgenii on 2009-10-13
Yes, i have the same problem. I've just upgraded to gnome 2.28, don't know if that has got something to do with it.
Thanks for the no_cookie tip though :)

---

### Post by oldos2er on 2009-10-13
> **pt123 said:**
> anyone else having troubles logging in with this application and have to resort to running it:
checkgmail -no_cookies

 This problem is fixed in the SVN version: [http://checkgmail.sourceforge.net/](http://checkgmail.sourceforge.net/)

---

### Post by NCLI on 2009-10-13
The easiest way to install the latest version of CheckGmail:

sudo apt-get install checkgmail && checkgmail -update

---

### Post by SomeGuyDude on 2009-10-13
> **hotweiss said:**
> Try it out. It is really convenient, you'll hate opening your browser to check your email after a while.

People have their browsers closed? :confused:

---

### Post by pt123 on 2009-10-14
> **NCLI said:**
> checkgmail -update
the update worked. But now when you click on the icon in the notification area it is not able to open the browser into your Gmail account loggen in. 

You still have to enter your password

---

### Post by pt123 on 2009-10-17
Using
**checkgmail --no-login**

solved the problem of gmail not being able to login from the browser but if you have logged out in the browser it can not log you in ( which it used)

---

### Post by rburkartjo on 2009-10-17
didnt for me will just mess with it until i can fix or install the one on awn that works with no problems

---

