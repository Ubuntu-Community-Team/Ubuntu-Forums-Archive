---
title: "DT's NoScript Configuration Guide"
date: 2011-11-12
forum: Security
---

### Post by Dangertux on 2011-11-12
I just posted this here... If someone thinks it needs its own thread  feel free to make it so or tell me to make it so and I'll make the  thread and delete this, it just isn't really Ubuntu-centric and its more  relevant to this discussion. 

P.S : If you guys like it I can jusjt copy paste it to the wiki ;-)

So yeah...lol.. Also the VUPEN thing -- You guys clearly haven't seen the new Chrome POC's. It's getting nasty (they're paying $1000+ for anyone who wants to do the research and submit POC though)
[B][SIZE=2]
DT's NoScript Configuration Guide[/SIZE][/B]

This is a quick run-through of configuring NoScript under Firefox. You can get NoScript here : [http://noscript.net/getit](http://noscript.net/getit)



Click the NoScript (S) icon next to your URL bar in firefox and choose "Options"


**[SIZE=2]General Tab[/SIZE]**

Default Settings are Fine

**[SIZE=2]Whitelist Tab[/SIZE]**

You should add a list of frequently visited sites that you trust. Please note Whitelisting a site will not stop NoScript from protecting you from XSS/CSRF and ABE violations (we'll explain this more later). You will notice there are already some sites whitelisted for you. If for some reason you do not trust those sites you may highlight them and click "Remove Site" and it will no longer be in the whitelist. You should add trusted top-level sites to make it easier.

Adding a whitelisted site

Simply type the domain of the site into the "Address of Website Bar" and click "Allow" example : [http://ubuntuforums.org](http://ubuntuforums.org) or ubuntuforums.org

[IMG]http://dangertux.no-ip.org/downloads/whitelist.png[/IMG]


After you have whitelisted the sites you commonly visit and trust you are done here.

Note : You need to weight the probability that the site is secure when whitelisting it. For example: [http://canonical.com](http://canonical.com) (probably okay) [http://superleethackersecrets.ru](http://superleethackersecrets.ru) (probably not so much) Keep in mind this is entirely subjective and unless you plan on running a vulnerability assessment against the site all you can do is trust the administration of that site.

[SIZE=2]**Embeddings Tab**[/SIZE]

[IMG]http://dangertux.no-ip.org/downloads/embeddings.png[/IMG]

This is an important tab and we will be modifying the default settings considerably here. Outside of the default settings you probably also want to place a check in the boxes ("Forbid <IFRAME>", "Forbid <FRAME>", "Forbid WebGL", "No placeholder objects from sites marked as untrusted"). Additionally for ease of use you may wish to choose "Collapse Blocked Objects" this doesn't add or detract security, it just makes sites displaying blocked cross site content display more clearly. 

"Apply these restrictions to Whitelisted Sites" : This should probably be left unchecked unless you are super paranoid and want to break all your favorite sites.

[SIZE=2]**Appearance Tab**[/SIZE]

This is entirely up to you, and depends on how you want NoScript to display itself. I leave it at default, and will not discuss it further here.

[SIZE=2]**Notifications Tab**[/SIZE]

This is how noisy NoScript is going to be. It will not change the amount of protection NoScript gives you, however it will tell you when NoScript alerts you or doesn't alert you to different blocked content or actions. The default settings are fine here as well.
[SIZE=2][B]
Advanced Tab[/B][/SIZE]

These are your advanced NoScript options and contain several sub tabs which we will go through now.
**Untrusted sub-tab**

[IMG]http://dangertux.no-ip.org/downloads/untrusted.png[/IMG]

For untrusted sites you will wish to place a check in the following boxes ("Forbid bookmarklets", "Forbid META redirections inside <NOSCRIPT> tags">
[B]
Trusted sub-tab[/B]

The default settings for this sub tab are acceptable so long as you are not "Trusting" sites that should not be trusted, refer to the same procedure as whitelisting.
[B]
XSS sub-tab[/B]

This tab allows you to configure your cross site scripting protection and whitelisting. It offers the ability for you to enter regular expressions for pattern matching of sites to trust cross site content from. By default the settings in the XSS tab are relatively secure. If you do not know regex I do not suggest attempting to learn here as a typo can lead you from trusting cross-site content from "look alike domains" like fakebook.com as opposed to facebook.com. If you wish to learn about basic regex here is a decent explanation : [http://linuxreviews.org/beginner/tao_of_regular_expressions/](http://linuxreviews.org/beginner/tao_of_regular_expressions/)

**HTTPS sub-tab**

This subtab allows you to force SSL on certain sites (of your choosing) as well as affect SSL cookie behavior. It has two sub-sub-tabs "Behavior" and "Cookies"
[U]
Behavior sub-sub-tab[/U]

[IMG]http://dangertux.no-ip.org/downloads/https.png[/IMG]

I would not recommend using "Force forbid active web content unless it comes from a HTTPS connection" as it will break the vast majority of websites. However I do recommend forcing HTTPS for sites where you store important information and or conduct financial transactions. In my example you can see I added my banks and social networking sites. You may type them in the pane seperating them with newlines. When you have done that move to the "Cookies" sub-sub tab.

_Cookies sub-sub-tab_

[IMG]http://dangertux.no-ip.org/downloads/https2.png[/IMG]

This sub sub tab allows you to force cookie encryption over SSL. All major sites should support this functionality, and as you can see from the example I added the same sites that I chose to force SSL for in the previous tab. You add them in the same manner. Once you are done we can move on to the ABE Tab
[B][SIZE=2]
ABE Tab
[/SIZE][/B]
This stands for Application Boundary Enforcement. This is one of the ways NoScript prevents things like NAT Pinning and some DNS based attacks. The default settings are fine, however its important to understand the major role this plays in your protection. I'm sure many of us know that 192.168.1.1 is a private address, meaning you might find it on your home network. Possibly your router's IP address. That being said, no internet based host should be sending anything to this address. If it is doing so it is likely attempting to use your machine as a relay to send code to another machine on your network, otherwise known as NAT pinning. That being said, if you are hosting a home server, this may cause issues if you are on the same network with the server, so don't freak out of if you get an ABE warning visiting your own website.
[SIZE=2][B]
External Filters Tab[/B][/SIZE]

Again the default settings here are fine. However, a brief overview of what this tab does, it allows you to create filters to block certain MIME types. For those who don't know a MIME type is essentially a file type. Like we all know .jpg is an image, or .fmv is a flash movie file. This allows you to set up filters based on those file types, on a site by site basis. This allows extremely fine grained control, so much so that we're not going to cover it here however if you would like to try to experiment I would suggest picking a content rich site and creating filters one by one to block all the content on the site but the static html. That should get you familiar with MIME type blocking.


After you are done configuring NoScripts Options, make sure "Forbid Scripts Globally" is Enabled (this will not effect your whitelisted sites). Restart your browser and surf safer :-)

---

### Post by CharlesA on 2012-01-20
Awesome job on the guide, DT. I have stickied it for now.

Maybe you can put it up on your site, or on the wiki.

---

### Post by Dangertux on 2012-01-20
> **CharlesA said:**
> Awesome job on the guide, DT. I have stickied it for now.

Maybe you can put it up on your site, or on the wiki.


This has been on my site for a while, thanks for the sticky. I meant to add it to the wiki forever ago and never got around to it. 

Hopefully I can get some time this weekend to knock that out.

DT \x00

---

### Post by Ms. Daisy on 2012-02-10
Hello. I put DT's NoScript Configuration guide into the Basic Security Wiki.  Maybe someone can proofread it for me?

I kind of hate the formatting I used, suggestions are welcome.

---

### Post by CharlesA on 2012-02-10
> **Ms. Daisy said:**
> Hello. I put DT's NoScript Configuration guide into the Basic Security Wiki.  Maybe someone can proofread it for me?

I kind of hate the formatting I used, suggestions are welcome.
Looks good from the glance I took of it. The double horizontal rules kinda look odd, but not too bad.

Maybe it would be better to have that one on it's own wiki page with a link from the BasicSecurity one?

---

### Post by CivilizationII on 2012-02-17
Thanks for the guide. A good starting point for a great security tool

---

### Post by Ms. Daisy on 2012-02-28
OK, this guide now officially lives on its own wiki page

[https://wiki.ubuntu.com/BasicSecurity/NoScript](https://wiki.ubuntu.com/BasicSecurity/NoScript)

---

### Post by Hungry Man on 2012-07-11
It's worth noting that you should probably use NoScript even if you whitelist globally. Less annoying but still helps keep things secure.

---

### Post by Buntu Bunny on 2012-08-30
Very helpful. Thanks.

---

### Post by MyTinFoilHat on 2013-01-11
Many thanks for the comprehensive guide. I appreciate all the time and effort that went into making this - and its corresponding wiki page. Now I can breathe a tad easier...

---

### Post by crossgraphicideas on 2019-04-12
Many thanks for the complete guide.

---

