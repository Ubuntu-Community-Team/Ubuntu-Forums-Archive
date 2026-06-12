---
title: "PDF Annotation Interoperability on Ubuntu and Android."
date: 2013-02-22
forum: The Cafe
---

### Post by donniezazen on 2013-02-22
Hello,

What applications can I use to annotate my PDFs on both Ubuntu and Android? I have been using Okular on Ubuntu which saves annotations as native document archive which can't be opened by Android app [ezPDF Reader.]("https://play.google.com/store/apps/details?id=udk.android.reader&hl=en")

Thanks.

---

### Post by mJayk on 2013-02-23
Hi,

I use RepliGo for my annotations in Android, it allows annotations that can be open and edited in standard PDF readers but it also allows you to "draw" on the pdf, especially helpful being a scientist.

Once the squiggles and annotations are done you can "save as" to a pdf and it keeps the normal annotations as annotations and saves the squiggles into the actual pdf.

Hope it helps

Matt

---

### Post by donniezazen on 2013-02-23
> **mJayk said:**
> Hi,

I use RepliGo for my annotations in Android, it allows annotations that can be open and edited in standard PDF readers but it also allows you to "draw" on the pdf, especially helpful being a scientist.

Once the squiggles and annotations are done you can "save as" to a pdf and it keeps the normal annotations as annotations and saves the squiggles into the actual pdf.

Hope it helps

Matt

There are a variety of choices on Android but are very limited on Linux. I couldn't find any options to highlight on Evince and Okular is great but a KDE apps are not my personal favorite and it hangs everytime I try to print something using it. The main problem is Okular annotates in a separate file called archive which can't be open in other PDF readers. It would be nice to have an application that works in Linux, Web for Chromebook and Android.

---

### Post by sudodus on 2013-02-23
I use a third program for that xournal

```
sudo apt-get install xournal
```

You can type and draw on a layer on top of the pdf page, save it in an own format (for further editing), and finally export it as a new pdf file.

---

### Post by donniezazen on 2013-02-23
> **sudodus said:**
> I use a third program for that xournal

```
sudo apt-get install xournal
```

You can type and draw on a layer on top of the pdf page, save it in an own format (for further editing), and finally export it as a new pdf file.

Thanks, its not the best solution. Okular now does save annotations in PDF but it will not work currently on Ubuntu 12.4/10. I will try to compile it and see if it works.

[http://askubuntu.com/questions/1529/how-can-i-highlight-pdfs](http://askubuntu.com/questions/1529/how-can-i-highlight-pdfs)
[https://bugs.launchpad.net/ubuntu/+source/okular/+bug/1031798](https://bugs.launchpad.net/ubuntu/+source/okular/+bug/1031798)
[https://bugs.kde.org/show_bug.cgi?id=151614](https://bugs.kde.org/show_bug.cgi?id=151614)

---

### Post by donniezazen on 2013-02-24
Okular 0.16 with poppler 0.20 does annotate in PDF. So the problem is solved. I hope Evince also implements a basic and must feature like this.

---

