---
title: "&quot;hplip-3.15.7.run&quot; file blocked for download by uBlock Origin due to Badware risks?"
date: 2015-08-05
forum: Security
---

### Post by patriot56 on 2015-08-05
Greetings all.
I am attempting to download the printer drivers for my HP Officejet Pro 6230 printer but when I attempt to download **hplip-3.15.7.run** from [[COLOR=#0000ff]http://prdownloads.sourceforge.net[/COLOR]]("http://prdownloads.sourceforge.net/hplip/") I am getting the following alert:
>      uBlock Origin has prevented the following page from loading:

     [http://prdownloads.sourceforge.net/hplip/hplip-3.15.7.run](http://prdownloads.sourceforge.net/hplip/hplip-3.15.7.run)
     
       Because of the following filter

     ||sourceforge.net^$other

Found in: uBlock filters – Badware risks     

I believe this is just a general alert from the browser add-on, **"uBlock Origin", **and I don't think this particular file has anything nefarious attached to it but, I want to be safe so I am posting this question here in an attempt to try to learn something about **Badware risks** and *how they apply* to Linux.  

I am using **LUbuntu 14.10** with **Firefox 39.0 **installed and the following security add-ons applied....**[COLOR=#008000]uBlock Origin 1.0.0.1[/COLOR],  [COLOR=#008000]NoScript 2.6.9.34[/COLOR], [COLOR=#008000]WOT 20150708[/COLOR]**

I hope this information is suitable and makes sense.  If I have left anything out please advise and I will include more information.

Thank you in advance for any help you can provide.

Regards

patriot2135

---

### Post by oldfred on 2015-08-05
Download directly from HP.

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by patriot56 on 2015-08-05
> **oldfred said:**
> Download directly from HP.

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

That's good advise **oldfred**.  Thank you.
I did try going to HP's web site originally but wasn't able to find a link to the driver that I needed; but, I was in a hurry at the time and didn't make much of an effort to keep looking so I just went to the next link in my search.

Guess I should'a just been patient and kept looking.  Thanks for the link. ;) and the advice.  I'll check it out.

Best Regards

patriot2135

---

### Post by oldfred on 2015-08-05
Only good advice if it works.

Not sure if your noscript settings may be part of issue, but I do not use that and have had no issues downloading directly from HP.
If an issue you may want to review noscript settings.

---

### Post by cariboo on 2015-08-05
uBlock, blocks any download from sourceforge.

---

### Post by patriot56 on 2015-08-06
> **cariboo said:**
> uBlock, blocks any download from sourceforge.

I wasn't aware of that. But I have heard that sourceforge has been responsible for the propagation of some "undesirable" and malicious programs.  I don't know if that is true or not but I don't like to take chances.
I migrated over to Linux from a lifetime of Winderz and I will admit, I am gun shy.  And still being relatively new to Linux I am still learning what is safe and what I should be careful of.:confused:

I *did* find a solution to the problem of getting the correct driver for this printer though.  I installed **hplip-3.14.x.x** from the repositories and it seems to work just fine; it's not the latest but it does allow me to use the printer and all of its features in Linux.
 
Thank you **cariboo**.  I appreciate your input. 

Respectfully,

patriot2135

---

### Post by patriot56 on 2015-08-06
> **oldfred said:**
> Only good advice if it works.

Not sure if your noscript settings may be part of issue, but I do not use that and have had no issues downloading directly from HP.
If an issue you may want to review noscript settings.

I think that the settings may be a part of the issue. I'm still learning how to use uBlock, I am very new to this add-on and will continue to research it.

I took your advice and went directly to HP's site and attempted the download from there.  I am still getting the same alert that I mentioned in my OP.
It looks like HP's is sending the **download request** to **sourceforge** for the actual download.  I don't think they are hosting it themselves.  I say this because uBlock is giving the same *source* URL as if I were trying to download from sourceforge.  

Anyhow, I did find a solution to this issue...I downloaded the appropriate HPLIP driver from the repositories. It isn't the latest one but it works to get the printer working under Linux. :D

I will, therefor, consider this topic Solved.

I really appreciate your and **cariboo's**  help regarding this issue.

Kindest Regards.

patriot2135

---

