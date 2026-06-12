---
title: "Filtering Google Image Search with DansGuardian"
date: 2013-04-02
forum: Ubuntu Christian Edition
---

### Post by davidkennedy85 on 2013-04-02
I felt like it was necessary to address this question as it is asked frequently on these forums and elsewhere. (I've asked it several times in several places myself.)

If you want to filter Google Image Search or force safe mode, then first you have to make Google Search use http as opposed to https. (The reason is clearly explained in the [DansGuardian Wiki]("http://contentfilter.futuragts.com/wiki/doku.php?id=two_configuration_families").)

As of the time of this edit, I'm only aware of a couple ways to accomplish this:

1. Block all https traffic.

2. Block google.com but allow nosslsearch.google.com.

3. If you are an administrator on your network, configure the DNS entry for [www.google.com](www.google.com) to be a CNAME for nosslsearch.google.com.

Option 1 is probably not a good idea if you ever do any banking, bill paying or shopping online. If you do any of these things over a standard http connection, then you are vulnerable to a man-in-the-middle attack. Anyone who wanted to could get your credit card number, social security number, or whatever other information you transmit by intercepting your http traffic.

Options 2 and 3 sound good but I haven't had time to verify whether they work or not. (For more information, see this [Google Support article]("http://support.google.com/websearch/answer/186669").)

Assuming that it's possible to force Google Search to use https, you could then add the following lines to the bannedregexpurllist to block Google Image Search altogether:

[FONT=courier new](google)+.*(tbm=isch)[/FONT]

You could also add this to the urlregexplist file to force safe mode on all searches (not just images):

[FONT=courier new]"(^http://.*\.google\..*/.*\?.*)"->"\1safe=on&"[/FONT]

Instead of blocking Google Image Search, you could tell it to append the original image URLs to the thumbnails in the results:

[FONT=courier new]"(^http://.*\.google\..*/.*\?.*tbm=isch.*)"->"\1surl=1&"[/FONT]

Then, you could filter the results based on the image URLs. (See this [Google Support article]("http://support.google.com/images/answer/1696900") for details.)

If you aren't able to force Google Search to use https, then the only other option I'm aware of is to block Google altogether.

The first time I posted this topic, I didn't realize there was a way to force Google Search to use https. I will continue to edit this as new information comes to light. Please let me know if I'm missing something.

Credit goes to Azrael84 for pointing this out.

---

### Post by arronwall1 on 2014-01-25
[COLOR=#000000]Hi, davidkennedy85.
I have googled it and found some [/COLOR][[COLOR=#000000]image filtering tutorials[/COLOR]]("http://www.yiigo.com/guides/csharp/how-to-filter-image.shtml")[COLOR=#000000] here. I hope it helps. Btw, I am also tesingabout the related [/COLOR][[COLOR=#000000]imaging programmes[/COLOR]]("http://www.yiigo.com/guides/vbnet/")[COLOR=#000000] these days. It seems that this one also allows image filtering work as well. Do you have any ideas about it? Or any good suggestion? Thanks in advance.



Best regards,
Arron[/COLOR]

---

