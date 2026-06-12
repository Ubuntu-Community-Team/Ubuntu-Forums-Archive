---
title: "Firefox 47 causing two flickers when going between instances."
date: 2016-06-16
forum: Ubuntu, Linux and OS Chat
---

### Post by mikodo on 2016-06-16
Hi,

Addendum:

I would like to delete this body of text as it is getting too wordy. But, that is against the rules of U. Forums.

Seems, I have stopped all the flickering as outlined below in all the web-pages I have tested, (most of the ones I go to regularly) and only Ubuntu Forums and Ubuntu ONE login seem to be still flickering.

1) Ubuntu Forums. If I open that page and then click on an icon to any other page in FF  there is no flickering. But, if I click on the FF radio button <- Go back one page, I get a black flicker on both sides of the page in the spaces on the outside of the main body of UF. They both have columns of 4 dots in them.

2) If I log into Ubuntu Forums with the Ubuntu One account, and it directs me back to Ubuntu Forums, the whole page flickers black for a millisecond before Ubuntu Forums is displayed again.

So, I am at a loss as to what this is. I am not sure it is FF's update to 47 has caused this alone or if it is  involved in conjunction with what is different specifically with Ubuntu Forums and Ubuntu One.

......................

Original text body:

I received the Ubuntu update to FF 47 yesterday. Since then, I noticed 'two' one millisecond display flickerings when going between open FF instances. I use Xubuntu 14.04.1 and use only the on-board Intel Integrated graphics. I have followed posts here over the years for ways to speed up FF and in many instances it entails shutting off new features Mozilla keeps adding to FF. There are too many to mention here. 

Here are the Release notes for FF 47. Does anyone see in the list of new things in FF 47 that might have caused this change of behaviour for me:

[URL="https://www.mozilla.org/en-US/firefox/47.0/releasenotes/"]https://www.mozilla.org/en-US/firefox/47.0/releasenotes/
[/URL]
I don't have any need for  window shadows and have never used  translucent panels, so, I shut off the Xfce compositor and that stopped  the flickering.

[http://docs.xubuntu.org/1404/settings-preferences.html](http://docs.xubuntu.org/1404/settings-preferences.html)

"*While Xubuntu doesn't come with many desktop effects, the Xfce compositor is enabled  by default. In the default Xubuntu configuration, the Xfce compositor is used to draw  shadows for windows and to enable translucent panels. If you have a low-end GPU or you don't like the desktop effects mentioned, you can turn off the compositor*".

There is no need to try to problem-solve this for me as, turning off the compositing fixed it for me. I could add a PCI-E GPU if it ever came to needing that but, I am about to retire this tower from being my main desktop machine. I am just curious if anyone knows what has caused  this behaviour in this FF update.

Thank you.

[URL="https://www.mozilla.org/en-US/firefox/47.0/releasenotes/"]

[/URL]

---

### Post by ScottSisco on 2016-06-23
This is because Firefox is no longer enabling xrender by default and eventually plan to eliminate the it completely from the browser. This is terrible terrible news for Linux users. See link below.

[https://www.reddit.com/r/firefox/comments/4nfmvp/ff_47_unbearable_slow_over_remote_x11/](https://www.reddit.com/r/firefox/comments/4nfmvp/ff_47_unbearable_slow_over_remote_x11/)

Fortunately, in the short term, you can still re-enable xrender by typing about:config in the url section of Firefox. Next search xrender and then you should see something called gfx.xrender.enabled. Change the value false to true and then restart Firefox. This should stop the flickering at least until you can no longer re-enable xrender. 


I work for a social services agency with a staff of over 500 employees all of which use Firefox running on Ubuntu terminals. Last Thursday, I upgraded one of our sites to from Firefox 46 to 47. After about two day's I had to move the site back to Firefox 46 because staff found it unusable. Now I need to write a script that will automatically force these settings into each users prefs.js file before I update each site. Super annoying.

---

### Post by mikodo on 2016-06-23
> **ScottSisco said:**
>  - what you said - 

Thank you.

This is going to sound a little strange and smacking of user error here. I installed Xubuntu 16.04 over the weekend since I started this thread. Now I have Xubuntu 14.04.1 and Xubuntu 16.04.0 dual-booting. I followed your instructions in about:config, (in fact a lot of the things I turn off is in there, ie. Pocket). I set  gfx.xrender.enabled -> true for both OS's.

In 14.04.1 

1. The flickering stopped when I logged into my Ubuntu One account to log into Ubuntu Forums.
2. It still flickers if I click on a FF page icon and then click the radio button in FF to return to the forums.

In 16.04.0

1. The flickering remained when I logged into my Ubuntu One account to to log into Ubuntu Forums.
2. It too, still flickers if I click on a FF page icon and then click the radio button in FF to return to the forums.

I made sure I completely logged out of FF after the changes in about:config and rebooted a couple of time to see that I am actually seeing different results for each install. I double checked each installs about:config gfx.xrender.enabled -> true settings.

My sympathies for your plight and work to make this work for your 500 desktop installs.

---

### Post by ScottSisco on 2016-06-23
I honestly have not messed around with Firefox 47 too much yet. My department is still using Firefox 46 and at the site having issues I simply rolled them back to using Firefox 46 which makes them happy for now. I did a little bit of testing of Firefox 47 on a test box I have and the workaround I outlined in above seemed to be a huge improvement so I posted it here, but I only spent about 10 minutes messing with it.

As far as performance based on Ubuntu version I've only tested it on 12.04. We are not even scheduled to deploy 14.04 for another few months. We generally stay a full LTS version behind in production. Our reasoning is by the time we deploy most of the kinks have been worked out and it makes a for a more stable environment.


I'll post back if  I make any other discovery's that lead to better performance.

---

### Post by mikodo on 2016-06-23
^^ Thank you, for posting any new revelations.

---

