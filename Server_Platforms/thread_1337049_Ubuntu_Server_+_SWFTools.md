---
title: "Ubuntu Server + SWFTools"
date: 2009-11-25
forum: Server Platforms
---

### Post by sTormDX on 2009-11-25
Hello!

- Ubuntu Server 8.04 64b
- SWFTools 0.8.1

I try to convert a pdf file with pdf2swf with that command :

```
pdf2swf mypdf.pdf -o myswf.swf
```I have no error, nothing and the swf file seems to be good because I can load it with firefox.

But after I wanted to had a player to that swf file so I use a template and I use that command :

```
swfcombine mytemplate.swf '#1'=myswf.swf -o finalswf.swf
```No error again. But when I load it on firefox the content is bad, I can not see pages anymore. The conversion gone wrong : I have black and white lines.

The fact is when I have done the same commands before on my Ubuntu desktop (local virtual machine) everything works. My final file is well and I can see my converted pdf.

I do not understand why in Ubuntu server that does not work!

NB: I use apt-get install swftools to add swftools files.

---

