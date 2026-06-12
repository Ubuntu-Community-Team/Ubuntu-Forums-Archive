---
title: "How to keep Facebook out"
date: 2013-02-08
forum: Security
---

### Post by mike acker on 2013-02-08
from an article on Wired This morning abou the fb glitch:

> Facebook provides code to embed widgets that display information such as  which of your friends like a site&#8217;s Facebook page, or which articles  have recently been &#8220;liked&#8221; by a friend. These widgets execute JavaScript  code in the user&#8217;s web browser that originates at Facebook, not the  site that the user is trying to view. The problem only seems to affect  users who are not logged into Facebook.q: how can we keep fb out out our computer and out of our life ?

reference

[http://www.wired.com/wiredenterprise/2013/02/facebook-widget-snafu/](http://www.wired.com/wiredenterprise/2013/02/facebook-widget-snafu/)

---

### Post by uRock on 2013-02-08
Use NoScript and right-click to select to block Facebook.

---

### Post by Cavsfan on 2013-02-08
^^ NoScript

Check out this link:

[[COLOR=blue]_Privacy addons for Firefox_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2102546")

You could also install the addon Collusion which shows how sites are interconnected.
Once you install the above addons you can look in Collusion to see that Facebook is no longer invasive.

---

### Post by SeijiSensei on 2013-02-08
I strongly recommend the **Ghostery** add-on for Firefox.  It blocks these kinds of tracking cookies and is much less annoying to deal with than NoScript.

---

### Post by uRock on 2013-02-08
> **SeijiSensei said:**
> I strongly recommend the **Ghostery** add-on for Firefox.  It blocks these kinds of tracking cookies and is much less annoying to deal with than NoScript.

Just installed and set that up. Thanx!

---

### Post by Cavsfan on 2013-02-09
I just installed Ghostery and disabled NoScript. We shall see how it goes. :)

---

### Post by Cavsfan on 2013-02-09
Nope Ghostery is not for me. :o I re-enabled NoScript. It may be a tad tedious but, once it is properly setup, you know what you have.
I like the ability to export/import NoScript's preferences so I don't have to start from scratch each time a Ubuntu is installed/re-installed. :)

---

### Post by uRock on 2013-02-09
> **Cavsfan said:**
> Nope Ghostery is not for me. :o I re-enabled NoScript. It may be a tad tedious but, once it is properly setup, you know what you have.
I like the ability to export/import NoScript's preferences so I don't have to start from scratch each time a Ubuntu is installed/re-installed. :)

I have never had to rebuild my Firefox with a new install. I keep a copy of my .mozilla file which is dropped into the Home folder of a new install. Ghostery's set up was very simple. Tick four or five boxes and let it go.

---

### Post by JKyleOKC on 2013-02-09
> **mike acker said:**
> q: how can we keep fb out out our computer and out of our life?I see that almost all the responses so far tell you how to keep it out of your browser, provided you use Firefox, but this does not keep it out of your computer.

If you feel confident using iptables, add a rule at the very front of the rule list to REJECT any packets from the IP range 31.13.64.0/18 and you will then never again process a single packet from the FaceBook server farm in Ireland. You may still, however, receive phish mail that claims to be from FaceBook -- but you can be confident that it's a spoofed "from" address.

---

### Post by 3v3rgr33n on 2013-02-09
I use SelfControl. I've been fb-clean for two weeks now.

Here's an OMGUbuntu article abt SelfControl [http://www.omgubuntu.co.uk/2011/02/self-control-ubuntu](http://www.omgubuntu.co.uk/2011/02/self-control-ubuntu)

---

### Post by Cavsfan on 2013-02-09
> **uRock said:**
> I keep a copy of my .mozilla file which is dropped into the Home folder of a new install. 

Thanks for that info! I still prefer NoScript because I am very familiar with it and have it on every install plus Windows 7.

That addon I mentioned in the 3rd post "facebook disconnect" will do as the OP is asking. 
It shows that it is blocking Facebook by the reload button on the right side of the address bar.
I use Facebook but not Twitter yet with the "twitter disconnect" addon I can see Twitter is trying to follow my every move. :shock:
The "google disconnect" addon can cause some problems with google related sites other than google itself but, I have had few problems.

---

### Post by QDR06VV9 on 2013-02-10
:guitar:> **uRock said:**
> I have never had to rebuild my Firefox with a new install. I keep a copy of my .mozilla file which is dropped into the Home folder of a new install. Ghostery's set up was very simple. Tick four or five boxes and let it go.

I use Ghostery & NoScript along with Flashblock with great sucess!
But the only Social Sites I vist are just Linux Forums.:lolflag:

---

### Post by sdowney717 on 2013-02-11
I generally dont use facebook. However I sometimes log into facebook, dont generally log out, and then see lots of sites where you can log into facebook. So does this mean Facebook is monitoring and watching every move I make? Does it stay logged in for days?

> **When you log in to Facebook, the service commences tracking your movements on every website you visit that supports Facebook Connect.** That's not just for sites that you've intentionally logged in to that day with your Facebook account, either. Also note that Facebook isn't necessarily just tracking which articles you Like, which images you Share, or which videos you Comment on; **it can track all articles you read, all the images you look at, and all the videos you watch.** That doesn't just include sites that have a Facebook Like button, either; some sites support Facebook Connect but give no overt sign of doing so. (Check out Business Insider's article from last September for more insight on how Facebook tracking works.)

[http://www.infoworld.com/t/internet-privacy/facebook-error-hijacks-thousands-of-websites-isnt-just-inconvenience-212518](http://www.infoworld.com/t/internet-privacy/facebook-error-hijacks-thousands-of-websites-isnt-just-inconvenience-212518)

---

### Post by haqking on 2013-02-11
> **sdowney717 said:**
> I generally dont use facebook. However I sometimes log into facebook, dont generally log out, and then see lots of sites where you can log into facebook. So does this mean Facebook is monitoring and watching every move I make? Does it stay logged in for days?



[http://www.infoworld.com/t/internet-privacy/facebook-error-hijacks-thousands-of-websites-isnt-just-inconvenience-212518](http://www.infoworld.com/t/internet-privacy/facebook-error-hijacks-thousands-of-websites-isnt-just-inconvenience-212518)


For chrome [https://chrome.google.com/webstore/detail/facebook-disconnect/ejpepffjfmamnambagiibghpglaidiec?hl=en](https://chrome.google.com/webstore/detail/facebook-disconnect/ejpepffjfmamnambagiibghpglaidiec?hl=en)

For Firefox [https://addons.mozilla.org/en-us/firefox/addon/fbdc/](https://addons.mozilla.org/en-us/firefox/addon/fbdc/)

[https://disconnect.me/tools](https://disconnect.me/tools)

---

### Post by sdowney717 on 2013-02-11
Thanks I installed the chrome add on. Reading the comments mentions people have some difficulty with facebook items after it installed.

---

### Post by Erik1984 on 2013-02-11
> **haqking said:**
> For chrome [https://chrome.google.com/webstore/detail/facebook-disconnect/ejpepffjfmamnambagiibghpglaidiec?hl=en](https://chrome.google.com/webstore/detail/facebook-disconnect/ejpepffjfmamnambagiibghpglaidiec?hl=en)

For Firefox [https://addons.mozilla.org/en-us/firefox/addon/fbdc/](https://addons.mozilla.org/en-us/firefox/addon/fbdc/)

[https://disconnect.me/tools](https://disconnect.me/tools)

Thanks!

---

### Post by Dry Lips on 2013-02-11
Ummm, and there's this as well: [https://www.facebook.com/help/224562897555674](https://www.facebook.com/help/224562897555674)

;)

---

### Post by neu5eeCh on 2013-02-11
There's also this:

[http://www.howtoforge.com/blocking-facebook-web-trackers-at-the-firewall-for-extra-privacy](http://www.howtoforge.com/blocking-facebook-web-trackers-at-the-firewall-for-extra-privacy)

Only recommended if, like me, you want nothing to do with Facebook. Nothing. What. So. Ever. :popcorn:

---

### Post by mörgæs on 2013-02-11
Threads merged.

---

### Post by haqking on 2013-02-11
> **sdowney717 said:**
> Thanks I installed the chrome add on. Reading the comments mentions people have some difficulty with facebook items after it installed.

people had problems with facebook items when using a tool that disconnects facebook ?

Are you sure ? LOL

---

### Post by Cavsfan on 2013-02-11
From post #3

[IMG]http://ubuntuforums.org/picture.php?albumid=1580&pictureid=8577[/IMG]

Even if you do not use facebook, twitter or google, they will follow you around. When they block a site, you will see it in the address bar at the right.

The Collusion addon shows how they are connected to everything without the addons as well as disconnected with the above addons installed.

If you do use facebook, F.B. Purity is also a good addon as it prevents many ads.

Myself I have not had any problems on Ubuntu or windows 7 with these 3 addons.

---

### Post by Soul-Sing on 2013-02-11
> **VTPoet said:**
> There's also this:

[http://www.howtoforge.com/blocking-facebook-web-trackers-at-the-firewall-for-extra-privacy](http://www.howtoforge.com/blocking-facebook-web-trackers-at-the-firewall-for-extra-privacy)

Only recommended if, like me, you want nothing to do with Facebook. Nothing. What. So. Ever. :popcorn:

this is how I do it.

---

### Post by HermanAB on 2013-02-16
How to keep FB out?  You could consider going retro and opening an account on Myspace instead...

---

### Post by Cavsfan on 2013-02-16
> **HermanAB said:**
> How to keep FB out?  You could consider going retro and opening an account on Myspace instead...

The only problem is that Facebook follows you even if you do not have a Facebook account. Twitter follows you.
Google follows you. They all track your browsing habits. If you used NoScript or Collusion addons you would see that.
I have no twitter account yet when I go to many websites, the twitter disconnect addon shows that twitter is requesting info. while surfing on an unrelated site.
On many websites I go to, it shows that all three are requesting info and the site I am on has nothing to do with any of them.

---

### Post by Lars Noodén on 2013-02-16
> **Cavsfan said:**
> The only problem is that Facebook follows you even if you do not have a Facebook account. Twitter follows you.
Google follows you. They all track your browsing habits. If you used NoScript or Collusion addons you would see that.
I have no twitter account yet when I go to many websites, the twitter disconnect addon shows that twitter is requesting info. while surfing on an unrelated site.
On many websites I go to, it shows that all three are requesting info and the site I am on has nothing to do with any of them.

You can [use iptables to block Facebook](http://www.howtoforge.com/blocking-facebook-web-trackers-at-the-firewall-for-extra-privacy) and the others.  I'm not sure how to get the AS number for the others, but the HowTo Forge example shows the one for Facebook in the comments.

---

### Post by Cavsfan on 2013-02-16
> **Lars Noodén said:**
> You can [use iptables to block Facebook]("http://www.howtoforge.com/blocking-facebook-web-trackers-at-the-firewall-for-extra-privacy") and the others.  I'm not sure how to get the AS number for the others, but the HowTo Forge example shows the one for Facebook in the comments.

Personally, I use Facebook. I do not want to block it. I could probably block twitter without any consequences.
Blocking google may have unintended consequences as it has so many tentacles into so may other things it's crazy.
Google is Youtube for example and I am sure there are many more so I would not think it would be wise to block that.

All I wanted after I found out Facebook, Twitter and Google follow you around nearly everywhere you go even when you are on other websites was to prevent that.
[COLOR="Blue"]Facebook Disconnect[/COLOR], [COLOR="Blue"]Twitter Disconnect[/COLOR] and [COLOR="Blue"]Google Disconnect[/COLOR] Firefox addons do just that. :D

Here is a picture of these three being blocked as it appears in the right side of my address bar:

[IMG]http://ubuntuforums.org/picture.php?albumid=2066&pictureid=8585[/IMG]
You can click on each and it will tell you what it is blocking giving you the opportunity to unblock that one.

Also, if you use Facebook and are tired of the ads, install [COLOR="Blue"]F.B. Purity[/COLOR] on Firefox and you'll see much fewer ads.

You can't even mention [COLOR="Blue"]F.B. Purity[/COLOR] on Facebook as it will be blocked and you could be banned I am not sure.

---

### Post by cetoka on 2013-02-18
Is using Facebook disconnect against the TOS of Facebook.I am an addictive Castleville player on Facebook and I do not want to be banned.

---

### Post by Cavsfan on 2013-02-19
> **cetoka said:**
> Is using Facebook disconnect against the TOS of Facebook.I am an addictive Castleville player on Facebook and I do not want to be banned.

I am not aware of it breaking their TOS. I have never had any problem as I don't think Facebook can detect that this Firefox addon is installed.

Plus I cannot see how they could have their TOS say anything about them being allowed to follow you around the internet on other sites besides Facebook.
That would appear to me to be an ethical issue.

If you try to mention the addon on Facebook, they may block you from doing so. I tried to mention to a friend on Facebook that the  **F.B. Purity** addon cuts out the ads but, Facebook would not allow me to post with that on it.
I have had that addon installed for a long time and at one time you could mention it.

---

### Post by CharlesA on 2013-02-19
> **SeijiSensei said:**
> I strongly recommend the **Ghostery** add-on for Firefox.  It blocks these kinds of tracking cookies and is much less annoying to deal with than NoScript.

Just wanted to say thanks. I installed it and had no idea sites uses so many different tracking junk.

---

### Post by cogset on 2013-02-21
> **JKyleOKC said:**
> I see that almost all the responses so far tell you how to keep it out of your browser, provided you use Firefox, but this does not keep it out of your computer.

If you feel confident using iptables, add a rule at the very front of the rule list to REJECT any packets from the IP range 31.13.64.0/18 and you will then never again process a single packet from the FaceBook server farm in Ireland. 

Right ;) and I would add to that IP also 31.13.64.0/24 , 69.171.224.0/19 and 66.220.144.0/20 so that it doesn't feel alone...

also adding these lines in your hostfile wouldn't hurt

 ```
127.0.0.1       facebook.com
127.0.0.1       facebook.net
127.0.0.1       fbcdn.net
127.0.0.1       fbcdn.com
```Speaking of Firefox,NoScript and Collusion are also excellent suggestions,I would also add Adblock to remove the ubiquitous fb-related widgets on  any webpage and then also block all 3d party cookies for good measure.

Modifying these preferences in **about:config** will also make life  hard for trackers in general :

**dom.event.clipboardevents.enabled **--> toggled to false will prevent websites from knowing  what content you have highlighted/copied on a webpage

**network.http.sendRefererHeader** --> set to 0 will not send the referer to the website,meaning it won't know from where you are coming, .i.e. it won't know from which other website you're visiting their page

**layout.css.visited_links_enabled**  --> toggled to false will prevent history sniffing

All of this suggestions can/will break some websites or some specific functionalities,so it will be up to you to choose which to use and how:especially blocking the referer will make logging to some websites impossible,which can be fixed using this addon [https://addons.mozilla.org/en-US/firefox/addon/refcontrol/](https://addons.mozilla.org/en-US/firefox/addon/refcontrol/)
if you install Collusion,you will probably see a maze of connections between various trackers in its graph,blocking 3d party cookies and the referer will basically zero it out...

---

### Post by uRock on 2013-02-21
> **cogset said:**
> Right ;) and I would add to that IP also 31.13.64.0/24 , 69.171.224.0/19 and 66.220.144.0/20 so that it doesn't feel alone...

also adding these lines in your hostfile wouldn't hurt

 ```
127.0.0.1       facebook.com
127.0.0.1       facebook.net
127.0.0.1       fbcdn.net
127.0.0.1       fbcdn.com
```Speaking of Firefox,NoScript and Collusion are also excellent suggestions,I would also add Adblock to remove the ubiquitous fb-related widgets on  any webpage and then also block all 3d party cookies for good measure.

Modifying these preferences in **about:config** will also make life  hard for trackers in general :

**dom.event.clipboardevents.enabled **--> toggled to false will prevent websites from knowing  what content you have highlighted/copied on a webpage

**network.http.sendRefererHeader** --> set to 0 will not send the referer to the website,meaning it won't know from where you are coming, .i.e. it won't know from which other website you're visiting their page

**layout.css.visited_links_enabled**  --> toggled to false will prevent history sniffing

All of this suggestions can/will break some websites or some specific functionalities,so it will be up to you to choose which to use and how:especially blocking the referer will make logging to some websites impossible,which can be fixed using this addon [https://addons.mozilla.org/en-US/firefox/addon/refcontrol/](https://addons.mozilla.org/en-US/firefox/addon/refcontrol/)
if you install Collusion,you will probably see a maze of connections between various trackers in its graph,blocking 3d party cookies and the referer will basically zero it out...
Too bad this actually breaks the Facebook page, which the OP has an account with.

---

### Post by scratman on 2013-02-21
My preferred method is to not have a Facebook account.

---

### Post by haqking on 2013-02-21
edit: ignore me ;)

---

### Post by cogset on 2013-02-22
Uh...I saw this > how can we keep fb out out our computer and out of our life ?and assumed he wished to get rid of it for good.

---

### Post by Erik1984 on 2013-02-22
> **CharlesA said:**
> Just wanted to say thanks. I installed it and had no idea sites uses so many different tracking junk.

The blocked JavaScript list from NoScript can be scary for some major tech oriented sites. Sometimes it doesn't even fit on the screen :P 

But it's quite a serious concern of mine that popular sites use so many external scripts that must run on my machine. If they pull in stuff from 10 different ad networks the chances that one of those serves malware increases as well.

---

