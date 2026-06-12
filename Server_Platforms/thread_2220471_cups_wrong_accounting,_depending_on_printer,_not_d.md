---
title: "cups wrong accounting, depending on printer, not driver"
date: 2014-04-28
forum: Server Platforms
---

### Post by huehnerhose on 2014-04-28
Hi,

I have an ugly problem figuring out why I can't track the printed pages right in cups.
My cups has to manage 2 Konica Minolta bizhub copier/printers. These two have enabled account tracking based on costcenters. For easy printer and driver delivery inside a Windows domain I chose to deploy custom PS drivers (made via PSCRIPT5* Windows drivers) and use a special "cups"-costcenter and account printing user based.

[http://casa.apertus.es/blog/2011/06/howto-account-tracking-konica-minolta-c220-under-linux/](http://casa.apertus.es/blog/2011/06/howto-account-tracking-konica-minolta-c220-under-linux/)
This Post suggested a way to get the costcenter authentification working. Another post somewhere else suggested adding *cupsFilter to the ppd to get the minolta filter working.

I thought I would get "correct" page count out of the PS printing. For my non-bizhub printer everything works great. But the bizhub printers only count to 1.

I thought it would be the pstops filter which didn't get called, but the debugging output says pstops is called. I really can't see a difference to the other printer where counting works.
Output here:
bizhub: 2 paged document, cups counts 1
[http://pastebin.com/k8mnLSSZ](http://pastebin.com/k8mnLSSZ)

other printer, 2 paged document, cups counts 3 (first time miscount registered on my side)
[http://pastebin.com/cLNZ7FYz](http://pastebin.com/cLNZ7FYz)


Any hints where to look?

Thanks! and best regards
Sebastian

---

