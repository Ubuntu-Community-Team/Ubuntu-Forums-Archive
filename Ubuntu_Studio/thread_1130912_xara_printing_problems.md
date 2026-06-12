---
title: "xara printing problems"
date: 2009-04-20
forum: Ubuntu Studio
---

### Post by natrixnatrix89 on 2009-04-20
Hi. I'm having no problems with printing in other programs, but whenever I try to print anything in xara (even just see a print preview) it crashes and says:
```
(xaralx:7099): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(xaralx:7099): GnomePrint-CRITICAL **: gnome_print_filter_reset: assertion `GNOME_IS_PRINT_FILTER (f)' failed

(xaralx:7099): GnomePrint-CRITICAL **: gnome_print_filter_flush: assertion `GNOME_IS_PRINT_FILTER (f)' failed

** (xaralx:7099): WARNING **: could not set the value of Settings.Document.Filter, node not found
Segmentation fault

```
I searched the xara forum and found a similar thread [here]("http://www.talkgraphics.com/showthread.php?t=36339").
the answer was
> The autopackage version of XaraLX is outdated. There have been so many updates to the wxWidgets and other needed libs since it was released.
Does Suse not have a current build of XaraLX within their repos?
If not, might I suggest making the request to update XaraLX in the Suse forums?
But i'm a newbie and don't understand, what does it mean..
Can anyone tell me if there is a way for me to solve this?

---

