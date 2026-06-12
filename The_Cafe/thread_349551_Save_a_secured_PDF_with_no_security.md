---
title: "Save a secured PDF with no security"
date: 2007-01-30
forum: The Cafe
---

### Post by btrotter on 2007-01-30
I am studying for a couple tests and have test material which is in PDF format. I am wanting to make my own study guide by extracting relevant material from the dozens of PDF's I have. However, some of the pdf's have it so that I can't copy from them.

Are there any tools that can open a pdf and either save it without the copy-protection turned on, or can I copy and paste from a secured pdf to another pdf without losing the formatting?

---

### Post by Steveire on 2007-01-30
Convert it to ps and back to pdf

---

### Post by btrotter on 2007-01-30
> **Steveire said:**
> Convert it to ps and back to pdf

What tool can do that?

---

### Post by burek on 2007-01-31
> **Steveire said:**
> Convert it to ps and back to pdf

In Linux, there is much easier & faster, dude !   lol
 
(forum policy)

---

### Post by btrotter on 2007-01-31
> **burek said:**
> In Linux, there is much easier & faster, dude !   lol
 
(forum policy)

Can you elaborate?

---

### Post by mcduck on 2007-01-31
> **btrotter said:**
> What tool can do that?

You'll need 2 tools, pdf2ps (converts from pdf to PostScript) and then ps2pdf (opposite of the first one).

Both tools are installed by default.

```

$ pdf2ps protecteddocument.pdf document.ps
$ ps2pdf document.ps document.pdf
```

---

### Post by PriceChild on 2007-01-31
Please first ensure that the material you are editing is not copyrighted... or that you have permissions from the author to copy it.

Which I assume it is seen as there's copy protection on it.

---

### Post by btrotter on 2007-01-31
mcduck, that did work, the only problem is that when it was imported back into pdf format the text is no longer selectable. It is like it did a print from the ps to pdf, so when I open the pdf, it is like I am opening an image of what the document used to look like.

Also PriceChild, this document is an company internal document from our training department. It was created close to 2 years ago and no one in our training or marketing departments can tell me how to unlock it or knows what the password would be.

---

### Post by burek on 2007-02-01
> **btrotter said:**
> Can you elaborate?

> Please first ensure that the material you are editing is not copyrighted... or that you have permissions from the author to copy it.

Which I assume it is seen as there's copy protection on it.

you see : 
no way to post things like this ... 
I got one penalty from prince child just for posting one JPEG on a rom website by accident...
They have high policy for the forums now ... only 

I just give you an hint that any convertions can reduce the quality of the pdf.... I can give you one pdf for instance, and this ps2pdf method will give you No Picture :-)

---

### Post by PriceChild on 2007-02-02
I'd appreciate it if you spelt my name right :) "PriceChild"

Not PrinceChild or Prince Child... and it has capitals :)

But anyway yeah... we don't want to get sued and so do not allow links to ANY illegal content :)

---

### Post by burek on 2007-02-02
Oup's, Sorry sorry for misspelling your name. :( 
[B]
PLEASE, Can this Thread be closed please for Illegal Contents & targets  ?[/B]

---

### Post by mips on 2007-02-02
> **burek said:**
> [B]
PLEASE, Can this Thread be closed please for Illegal Contents & targets  ?[/B]

But discussing and linking to win32codecs is ok ](*,)

---

### Post by HermanAB on 2010-03-30
Hmm, when all else fails, edit the file with a programmer's editor and delete the offending stanza - towards the end of the PDF document.

---

### Post by shakira 11 on 2010-03-30
It seems that this question has comfused many people.Save secured pdf use advanced word to pdf is quite common.

---

