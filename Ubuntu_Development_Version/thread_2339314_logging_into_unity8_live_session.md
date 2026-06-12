---
title: "logging into unity8 live session"
date: 2016-10-07
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-10-07
You can now logout of the ubuntu-desktop  yakkety release candidate "live" session and log on to unity8 session. When you log off from your unity8 session you can log back in to ubuntu-desktop and all work you have done/downloaded and saved will still be there.

regards..

---

### Post by CantankRus on 2016-10-07
First look......
Installed libertine but fails to create a container.
Is installing libertine all I need do to get going or is there something else that 
needs to be installed?

---

### Post by ventrical on 2016-10-07
> **CantankRus said:**
> First look......
Installed libertine but fails to create a container.
Is installing libertine all I need do to get going or is there something else that 
needs to be installed?

Libertine and libertine-scope ... but libertine will not wok in unity8 on live session... only on hard install... one of those things eh :)

edit:  It might be interesting experiment to use mkusb to make a persistent drive and then see if libertine will work under that environment.

regards

---

### Post by CantankRus on 2016-10-07
I have installed the latest daily and updated.
Libertine and libertine-scope are installed.
But when I run libertine I get the create container window and it begins to create but then fails.
Is there anything else I need to do after a fresh install.
Any guide anywhere? 
Thanks.

---

### Post by ventrical on 2016-10-07
> **CantankRus said:**
> I have installed the latest daily and updated.
Libertine and libertine-scope are installed.
But when I run libertine I get the create container window and it begins to create but then fails.
Is there anything else I need to do after a fresh install.
Any guide anywhere? 
Thanks.

After my install of the release candidate - amd64 ubuntu-desktop I installed libertine through unity7 and I ran libertine through unity7  and it installed my container flawlessly. Then I could go to unity8 and experiment installing apps.

I had just tried on persistent drive created with mkusb and libertine fails perhaps due to a policy-kit problem. But I have a fresh install from yesterday's release and it works so far, so good.

Regards..

---

### Post by CantankRus on 2016-10-07
Libertine fails in Unity7 as well.
Think I'll just leave it 'til Yakkety is released and try again.
One question...I've got the Yakkety daily ISO zynced.
Will that just keep updating until it reaches the same version as the release candidate?

---

### Post by ventrical on 2016-10-07
> **CantankRus said:**
> Libertine fails in Unity7 as well.
Think I'll just leave it 'til Yakkety is released and try again.
One question...I've got the Yakkety daily ISO zynced.
Will that just keep updating until it reaches the same version as the release candidate?

Yes. I have done the same as you.  I wrongly stated that the RC was released yesterday but I now understand that it will be later today or early Saturday so keep zsyncing over the next 48 hours and you will have a fully fledged RC.

[https://www.youtube.com/watch?v=QAveLtRD9kM&feature=youtu.be](https://www.youtube.com/watch?v=QAveLtRD9kM&feature=youtu.be)

Regards..

---

### Post by ventrical on 2016-10-07
> **CantankRus said:**
> Libertine fails in Unity7 as well.
Think I'll just leave it 'til Yakkety is released and try again.
One question...I've got the Yakkety daily ISO zynced.
Will that just keep updating until it reaches the same version as the release candidate?

Just noticing your tag line about nVidia driver. There is no way that I know of to get unity8 to run with nVidia driver. Are you using the nVidia driver on your unity8 installs?

Regards..

---

### Post by CantankRus on 2016-10-07
> **ventrical said:**
> Just noticing your tag line about nVidia driver. There is no way that I know of to get unity8 to run with nVidia driver. Are you using the nVidia driver on your unity8 installs?

Regards..
No, I left it with nouveau.
Eventually got containers to work by installing synaptic in unity7 and searching for libertine and installing all shown.
[ATTACH=CONFIG]271536[/ATTACH]

Unity8 is intersting but the whole concept is giving me itchy feet.
Do you know what release Unity8 is planned for?

---

### Post by ventrical on 2016-10-07
> **CantankRus said:**
> No, I left it with nouveau.
Eventually got containers to work by installing synaptic in unity7 and searching for libertine and installing all shown.
[ATTACH=CONFIG]271536[/ATTACH]

Unity8 is intersting but the whole concept is giving me itchy feet.
Do you know what release Unity8 is planned for?

it is planned as alternate for this release and perhaps default during Zesty Zebra. (my guess) :)

---

### Post by ventrical on 2016-10-07
> **CantankRus said:**
> No, I left it with nouveau.
Eventually got containers to work by installing synaptic in unity7 and searching for libertine and installing all shown.
[ATTACH=CONFIG]271536[/ATTACH]

Unity8 is intersting but the whole concept is giving me itchy feet.
Do you know what release Unity8 is planned for?



Just an add on here... unity8 *is* interesting in that it allows us to use the virtual features of our Intel processors in a very sleek and efficient way by using lxc containers. This allows us to run xapps concurrently from separate containers without the hassle of loading up a full Virtual Box GUI.

Regards...

---

