---
title: "Trick: Firefox: click to select url in address bar"
date: 2006-08-03
forum: Tutorials
---

### Post by Jose Catre-Vandis on 2006-08-03
In Windows, the default for Firefox is to select the entire url in the address bar when you single left click into it. Under Ubuntu, this doesn't happen, and you have to double click. If you use Firefox in both OS on a regular basis then this tip might help to avoid some annoyance.

Open Firefox

type:
```
about:config
```
in the address bar and click Go (or press Enter/Return)

In the filter box type:
```
click
```
From the filtered list you need to work with:
```
browser.urlbar.clickSelectsAll
```
Right click on this entry and select "Toggle" from the drop down menu, to change the value to "true"

Close Firefox

Re-open Firefox and single left click in the address bar, you should find the entire url is selected :-)

Of course, if you prefer the Ubuntu default action, then do the reverse in your Windows Firefox :-)


EDIT:

I have collected together the other keyboard shortcuts available for working with the address and search bars, Thanks to everyones contribution to make my trick more complete, and to ***morfeibg*** for gathering them together
```
Here are the other helpful shortcuts that were posted:
Ctrl + L - selects the URL address
Ctrl + I - shows page information
Ctrl + K - selects the text in the search bar
Hitting Esc when the pointer is in the address bar selects the url
```

---

### Post by Ferio on 2006-08-04
Though I abandoned Windows more than a year ago, I missed this behaviour in my Firefox, thank you very much!

---

### Post by darrenrxm on 2006-08-04
I found this to be vexing when I first started using firefox on Ubuntu. But then I stared using the cntl+l shortcut. Anyway, this should help windows users.

---

### Post by vdemeester on 2006-08-04
> **darrenrxm said:**
> I found this to be vexing when I first started using firefox on Ubuntu. But then I stared using the cntl+l shortcut. Anyway, this should help windows users.

Wouah, i didn't notice this key shortcut. Very useful ^^

---

### Post by vuitton on 2006-08-04
thank you very much : ) i missed this 'feature'

---

### Post by pjot on 2006-08-04
I've always felt that Firefox was clumpsy on MS and never really figured out why but when I saw this thread I realized that's the main issue I've had with MS FF so I've done the reverse and now FF feels (almost ;)) as good on MS.

---

### Post by bionnaki on 2006-08-04
thanks!

---

### Post by Rackerz on 2006-08-04
Thanks for this! I missed it :D.

---

### Post by deepank on 2006-08-04
I had just started using firefox in ubuntu and was missing this( I was actually selecting the url by click and drag ... most troublesome) . Thanks for the cool tip.

---

### Post by zerwas on 2006-08-04
Perhaps you could add this at the end of your trick:
I think selecting the url in address bar can better be done by pressing Escape. Because the url, that has selected by this way, does not get the way into the clipboard! In my opinion this is better for copy and paste actions.
[LIST=1]
[*]single click in the address bar
[*]pressing Escape
[/LIST]

Greetings,
zerwas

---

### Post by Tomosaur on 2006-08-04
Thanks for this, made my life just a little bit easier :P

---

### Post by PingunZ on 2006-08-04
try Ctrl + L

---

### Post by thunderduck3141 on 2006-08-04
if find that trying to make linux and linux apps more windoz like defeats the purpose of linux
we should be setting the standards not them

---

### Post by Tomosaur on 2006-08-04
Can't help but feel we're a little late for that :P

---

### Post by lucia_engel on 2006-08-04
> **Jose Catre-Vandis said:**
> In Windows, the default for Firefox is to select the entire url in the address bar when you single left click into it. Under Ubuntu, this doesn't happen, and you have to double click.

Under Ubuntu (I think this works in Windows too), I just click the little icon next to the url bar to select the address.

BTW, does anyone know an efficient method (ie. one click) to "select all" the search box? I know you can right click and select all or just choose a search engine from the list to select all.

---

### Post by zerwas on 2006-08-04
> **lucia_engel said:**
> Under Ubuntu (I think this works in Windows too), I just click the little icon next to the url bar to select the address.

Thanks, didn't know that!
> **lucia_engel said:**
> 
BTW, does anyone know an efficient method (ie. one click) to "select all" the search box? I know you can right click and select all or just choose a search engine from the list to select all.
:D Do the same like you do with the url bar: click the Google-icon.

---

### Post by Jose Catre-Vandis on 2006-08-04
> **thunderduck3141 said:**
> if find that trying to make linux and linux apps more windoz like defeats the purpose of linux
we should be setting the standards not them

FCOL :-({|= 

The point of the tip/trick was to align functionality/usability - either way for Windows or Linux preference, as there are probably many folk like me who use Windows and Linux in their daily work/home lives.

What vexes me is why the settings are different for each OS, probably to ease the transfer of IE users over to FF, otherwise I am sure Mozilla would have the default settings the same

---

### Post by lucia_engel on 2006-08-04
> **zerwas said:**
> Thanks, didn't know that!

:D Do the same like you do with the url bar: click the Google-icon.

Oh, but when I click on the google icon, it only shows the drop down menu of all the search engines I have. Though if I choose Google again from the menu then it'll "select all".

---

### Post by Sam on 2006-08-04
IMO I find better one click to select, double click to select all. Because with one click you can select a part of the URL to edit something, and with double click to replace the whole stuff. Anyway that's the way I prefer, and nobody thinks the same...

By the way, clicking the favicon will select the whole URL.

---

### Post by mustang on 2006-08-05
Cool tip. Thank you

---

### Post by kingbilly on 2006-08-05
This is a very helpful tip for the people I have shared linux with.  We go out to eat twice a week and this was the most recent topic we discussed.
My peers rarely edit the url in the address bar (.htm to .html?) but instead click in there to change the whole url.  Glad I noticed this on the front page of the forums, I will send it to those who needed it.
 
>  if find that trying to make linux and linux apps more windoz like defeats the purpose of linux
we should be setting the standards not them

Not sure if I agree with this.  Some standards are just, standard, in some cases and this is one of them (though I am a keyboard maniac and use Ctrl L as someone pointed out in this thread).  I don't know if we want to "Set" a standard in this case, which would look like this:

Ubuntu Linux - The OS for people who prefer to triple click in the address bar.  100% original, accept no substitutes. :rolleyes:

---

### Post by Van_Gogh on 2006-08-05
I've always been annoyed by the difference in Firefox bahaviour in windows and Ubutnu, so I think this is a really great tip.

Another small tip is that you can change it programatically too, if you want to change it for the default value for every user on the computer by changing the firefox.js file in the /usr/share/firefox/defaults/pref directory: Just change the false in
```
user_pref("browser.urlbar.clickSelectsAll", false);
```
to 'true'.

Don't know if that was useful for anyone, but now you know :-p

---

### Post by PingunZ on 2006-08-05
for selecting the whole text in the search bar do Ctrl + K

---

### Post by Adrian_b on 2006-08-05
They probably disabled that feature for Linux because of it's "select to copy" nature..
If you selected something and clicked in the URL bar to delete it, you would've lost the thing you copied before..

---

### Post by Xera on 2006-08-05
thanks, this was really annoying me having to highlight the url ;)

---

### Post by rko618 on 2006-08-05
Thanks! I've been looking for this for a long time.

---

### Post by morfeibg on 2006-08-06
Very useful how to.
Here are the other helpful shortcuts that were posted:
Ctrl + L - selects the URL address
Ctrl + I - shows page information
Ctrl + K - selects the text in the search bar
Hitting Esc when the pointer is in the address bar selects the url

---

### Post by vdemeester on 2006-08-06
> **morfeibg said:**
> Very useful how to.
Here are the other helpful shortcuts that were posted:
Ctrl + L - selects the URL address
Ctrl + I - shows page information
Ctrl + K - selects the text in the search bar
Hitting Esc when the pointer is in the address bar selects the url

Using keyboard is faster than click and double clicking everywhere.. Now i'm more and more efficient with keyboard in my firefox (under any OS)

---

### Post by Jose Catre-Vandis on 2006-08-06
> **vdemeester said:**
> Using keyboard is faster than click and double clicking everywhere.. Now i'm more and more efficient with keyboard in my firefox (under any OS)

This all depends on whether you have your hand/s on the mouse or the keyboard ;)

---

### Post by lbo on 2006-08-19
> Another small tip is that you can change it programatically too, if you want to change it for the default value for every user on the computer by changing the firefox.js file in the /usr/share/firefox/defaults/pref directory: Just change the false in
Code:

user_pref("browser.urlbar.clickSelectsAll", false);

to 'true'.

Thank you very much Van_Gogh, this was very useful for me. I needed to slightly modify this and replace "user_pref" with "pref" in order to make it work for me:

```
pref("browser.urlbar.clickSelectsAll", true);
```

The system-wide firefox.js was located at ```
/etc/mozilla-firefox/pref/firefox.js
``` on my Breezy installation with FireFox 1.07.

Kind regards,
Lambert

---

### Post by shadowfx78 on 2006-08-19
Thanks this works excellent

---

### Post by GotGamble on 2006-10-12
Thanks for the tip,was handy, plus I learned a little more about how to handle more advanced configuration problems with Firefox on Ubuntu.

You da man!

---

### Post by VenQWish on 2006-12-14
Thanks, this was really helpfull. I didn't see this in the original post, so I'll say it here. Pressing F6 also takes you to the url bar.

Another tip for migrating windows users (such as me ;) ). In the about.config, type in backspace as the filter, and set the value of browser.backspace.action to 0 to enable using backspace as a "back button".

---

### Post by stathiz on 2008-04-20
thanks for the tips :guitar:

---

### Post by PinkFloyd102489 on 2008-04-21
Also, you can restore the Backspace function in Ubuntu Firefox too. When you hit Backspace, it goes back a page instead of just acting like Page Up.


Search "backspace" in about:config and change the only entry there from "1" to "0" as in zero.

---

### Post by dage on 2008-04-23
> **zerwas said:**
> Perhaps you could add this at the end of your trick:
I think selecting the url in address bar can better be done by pressing Escape. Because the url, that has selected by this way, does not get the way into the clipboard! In my opinion this is better for copy and paste actions.
[LIST=1]
[*]single click in the address bar
[*]pressing Escape
[/LIST]

Greetings,
zerwas

not bad at all, thank u :)

---

### Post by kevinamadeus on 2008-05-26
Yay!
Thanks Jose. I'm a complete newbie and spent ages trying to figure this one out.

---

### Post by phyrewall on 2010-01-22
Thanks for this, it had bothered me a lot in the past, and even more so know that I've integrated the search bar into the address bar!

---

### Post by rahul_does on 2011-10-10
YTM,n,D!  This was such a pain!  Thanks a tonne, Angel!

---

