---
title: "Flight 4 Takes Off"
date: 2006-02-19
forum: The Fridge Discussions
---

### Post by TheFridge on 2006-02-19

	 <p>The fourth test release of the upcoming &#8220;Dapper Drake&#8221; has <a href="https://lists.ubuntu.com/archives/ubuntu-announce/2006-February/000050.html">been announced</a>. This is the debut of the new graphical installer, dubbed Espresso, which adds an icon to the desktop that allows users to permanently install Ubuntu right from the Live CD. A nicer tour of the new features <a href="https://wiki.ubuntu.com/DapperFlight4">is available</a> on the wiki. You can also follow the progress of Dapper development in Jane Weideman&#8217;s latest <a href="https://lists.ubuntu.com/archives/ubuntu-devel-announce/2006-February/000080.html">status update</a>.</p>
 

	**[Link To Original Article]("http://fridge.ubuntu.com/node/270")**
	

---

### Post by Foaming Draught on 2006-02-22
If I read Martin Pitt's few lines in Jane Weideman's update article correctly, he's not going to bother fixing CUPS until at least Dapper +1.
Is Dapper really going to be released without a print facility? If this doesn't fall into the category of regression, I don't know what does.
Can you imagine the reviews? Slashdot will have a field day.  "Not only is Dapper free, but you can save more money by selling your printer on eBay. You won't be able to use it".
Please tell me that I misunderstand Martin's paragraph in the status report, and please tell me that Dapper's cupsys will start recognising local printers soon. Fine as Breezy is, I'll migrate to FC5 or SuSE 10.1 if Dapper printing doesn't get fixed.

---

### Post by castrojo on 2006-02-22
From looking at [https://wiki.ubuntu.com/AutomaticPrinterConfiguration](https://wiki.ubuntu.com/AutomaticPrinterConfiguration) it looks as though the spec covers "zero configuration" of local USB printers.

As it stands now with breezy you plug in a USB printer, then go into the GUI tool and add the printer manually, choosing its model and type, etc. This spec appears to cover making all that automatic. I think that's the part being defferred, not the entire print functionality.

---

### Post by Foaming Draught on 2006-02-22
Yep, I'm quite happy with configuring my printer in Breezy. But if Dapper doesn't show on the cupsys GUI the printers which HAL and lsusb know all about, so that we can't use a local printer, then that strikes me as a regression, not just from Breezy but from most distros of the past couple of years.
We're on the fourth alpha and still no local printing. And still no acknowledgment of so many posts on the forums and Malone  from so many people.

---

### Post by nocturn on 2006-02-22
[QUOTE=Foaming Draught]Yep, I'm quite happy with configuring my printer in Breezy. But if Dapper doesn't show on the cupsys GUI the printers which HAL and lsusb know all about, so that we can't use a local printer, then that strikes me as a regression, not just from Breezy but from most distros of the past couple of years.
We're on the fourth alpha and still no local printing. And still no acknowledgment of so many posts on the forums and Malone  from so many people.[/QUOTE]

I haven't tried Dapper yet, so I'm somewhat confused.

Do you mean that the function of selecting the driver for a local printer from the GUI that is currently in Breezy is no longer working in Dapper?

---

### Post by Foaming Draught on 2006-02-22
Yes, that's precisely what I mean. GUI printer selection is fine under Breezy, but non-existent under Dapper. The problem is common to KDE and GNOME. Malone bug reports on the topic are too numerous to list here, as are forum posts.
I have been steadily more unhappy with a complete absence of response from Martin Pitt, the supposed lead for CUPS in Dapper. That's why his paragraph in Jane Weideman's latest update rang alarm bells. Of course we can live without automatic configuration, but not without any local printing at all.
The usual parade of old soldiers turns out when I post about this on other forums, telling me that I should use some command line routine which worked for them with a line printer and DEC PDP11 in 1980.

---

### Post by nocturn on 2006-02-22
[QUOTE=Foaming Draught]Yes, that's precisely what I mean. GUI printer selection is fine under Breezy, but non-existent under Dapper. The problem is common to KDE and GNOME. Malone bug reports on the topic are too numerous to list here, as are forum posts.
I have been steadily more unhappy with a complete absence of response from Martin Pitt, the supposed lead for CUPS in Dapper. That's why his paragraph in Jane Weideman's latest update rang alarm bells. Of course we can live without automatic configuration, but not without any local printing at all.
The usual parade of old soldiers turns out when I post about this on other forums, telling me that I should use some command line routine which worked for them with a line printer and DEC PDP11 in 1980.[/QUOTE]

I can't believe it?

Are they really considering to release Dapper with no functional printer config at all?

Dapper is supposed to go up against Vista...   I cannot imagine the negative reviews Ubuntu will get for this.

---

### Post by nocturn on 2006-02-22
Is there already a bugreport on this one?

---

### Post by Foaming Draught on 2006-02-22
Multiple reports, under multiple headings of CUPS, printing, specific printer, whatever.  Give me a mo, I'll compile a list.  And multiple posts on the Dapper forum. Nary an acknowledgment to any of them.

---

### Post by nocturn on 2006-02-22
[QUOTE=Foaming Draught]Multiple reports, under multiple headings of CUPS, printing, specific printer, whatever.  Give me a mo, I'll compile a list.  And multiple posts on the Dapper forum. Nary an acknowledgment to any of them.[/QUOTE]

And the responses to those reports?  I mean, if printing is completely broken in Dapper, that should be considered a showstopper bug...

---

### Post by az on 2006-02-22
[QUOTE=Foaming Draught]I have been steadily more unhappy with a complete absence of response from Martin Pitt, the supposed lead for CUPS in Dapper. That's why his paragraph in Jane Weideman's latest update rang alarm bells. .[/QUOTE]

Relax.  We are so far away from release to worry about things like this.

---

### Post by bonzodog on 2006-02-22
Are you referring to this:?
> 
automatic-printer-conf pitti 2
Medium Deferred Deferred
Was: requires a fair amount of new code and work, I'd rather make cups less buggy than add hal-cups-utils and try to integrate it; it would probably require sb who knows more about gnome than me anyway. Hopefully somebody comes along and gives gnome-cups-manager some love. Now: automatic-printer-conf:
no blocks, no time, deferred to dapper+1.


If so, he's talking about AUTOMATIC printer configuration (i.e not manual). This means we will still be able to configure manually, with the GUI front end.

---

