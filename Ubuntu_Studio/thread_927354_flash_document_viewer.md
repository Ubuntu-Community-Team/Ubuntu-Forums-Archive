---
title: "flash document viewer"
date: 2008-09-22
forum: Ubuntu Studio
---

### Post by slumbergod on 2008-09-22
hi all,

I have been searching the net for support on flash in an open source environment but there is very little available.

I have some pdf documents I want to covert to flash so I can serve them on a site. No problem there, pdf2swf works perfectly, except that it doesn't give me any document controls like next and previous. 

Extensive searching online has lead me to find FDviewer which acts as a wrapper for my swf documents, giving them the functionality they need. But, the Firefox flash plugin gives warnings about the resulting swf files wanting to access the internet.

Does anyone have any experience with FDviewer? I am not a flash developer and gievn the lack of *anything* to do with flash on the Linux platform, trying to teach myself isn't worthwhile. 

I looked at djvu but the Firefox plugin doesn't even work (FF3.01+Xubuntu).

Any suggestions?

---

### Post by slumbergod on 2008-09-23
Ok, I have managed to get my pdf document running perfectly with the rfxview flash viewer now. FDviewer is still the better one aestheitically and functionally (you can enter a page number to go straight to it).

Maybe someone who knows about Flash programming can just comment on the security warning I get when I use FDviewer.swf. The browser's Flash plugin (10RC2) throws a warning about the application trying to connect to localhost. Rfxview.swf does not do this.

Unfortunately, I know nothing about Flash programming and if I can get my documents to work with the viewer correctly, that is as far as I need to go.

Any thoughts on the localhost error?

---

### Post by paulmerchant on 2008-09-23
I've never used FDviewer, but if you read the swftools documentation (pdf2swf), you should see a way that you can add the controls you need. You can even create your own controls and compile them into your final swf.

---

### Post by slumbergod on 2008-09-23
Thanks, I have read the documentation several times. The only references to viewers mentioned are that you can use the default one (which is just a forward and backward button overlay) or create your own.

Unfortunately, my skills don't extend that far. I just need to find a freely availabe viewer so I can use that.

---

