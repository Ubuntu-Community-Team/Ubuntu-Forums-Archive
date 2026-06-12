---
title: "LibreOffice Problem in Quantal Quetzal"
date: 2012-10-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mmasroorali on 2012-10-15
I was hoping that the problem will be solved any day. However, with only three days left before the final release, I thought that I must report the problem.

In Quantal Quetzal I have observed the following problems with LibreOffice,
[LIST=1]
[*]Let us say I have already opened a file. When a second file in opened, and the cursor is moved to top, the top menu (File, Edit, View, Insert...) does not (often) appear in the second one. It appears, sometimes, when I wait for a few minutes. And sometimes, when the first file is closed.
[*]When the submenu (e.g. Format->Cells) is selected, the subsequent window does not appear.
[*]LibreOffice often crashes.
[*]When File->Close is selected, the file does not close. The cross button works however.
[/LIST]

These problems occur at random.

These problems are unique to LibreOffice.

I am using Ubuntu 12.10 (QQ) in my office machine. Updates are run daily.

I use 12.04 (PP) in my home machine and the above problems are not there.

---

### Post by dino99 on 2012-10-15
some questions:
- 32 or 64 bits install ?
- which DE : unity, GS, GC ?

here i have no issue with i386 on GC

---

### Post by grahammechanical on 2012-10-15
I am having similar issues. I am using Unity.

I think the problem is with Writer. I just opened Libreoffice this is what happened.

1) Opened Writer. Used File>Recent documents to open a document. OK.

2) Tried to use File>Recent Document to open a second document - All the menu labels would highlight as the mouse moved over them but the menus did not appear. This did not happen with the app-indicatior menus on the right.

3) Opening and closing Writer did not rectify the problem. So, was unable to open any documents using Writer.

4) Open Calc and was able to use File>Recent documents to open Writer documents.

I use Insert>Special characters a lot. On Saturday the special character utility stopped working in one of the two documents I had opened but was still working in the other opened Writer document. I had to close Writer to correct this problem but it happened again.

I have also noticed that after opening a Writer document the Copy icon does not activate until a few tenths of a second have passed. Then it continues working as it should.

Regards.

---

### Post by mmasroorali on 2012-10-15
> **dino99 said:**
> some questions:
- 32 or 64 bits install ?
- which DE : unity, GS, GC ?

here i have no issue with i386 on GC

32, Unity

---

### Post by mmasroorali on 2012-10-15
> **grahammechanical said:**
> I am having similar issues. I am using Unity.

I think the problem is with Writer. I just opened Libreoffice this is what happened.

1) Opened Writer. Used File>Recent documents to open a document. OK.

2) Tried to use File>Recent Document to open a second document - All the menu labels would highlight as the mouse moved over them but the menus did not appear. This did not happen with the app-indicatior menus on the right.

3) Opening and closing Writer did not rectify the problem. So, was unable to open any documents using Writer.

4) Open Calc and was able to use File>Recent documents to open Writer documents.

I use Insert>Special characters a lot. On Saturday the special character utility stopped working in one of the two documents I had opened but was still working in the other opened Writer document. I had to close Writer to correct this problem but it happened again.

I have also noticed that after opening a Writer document the Copy icon does not activate until a few tenths of a second have passed. Then it continues working as it should.

Regards.

I was trying to find a link between Calc and Writer usage at the same time. But can not exactly pin down the relation.

All my LO invocations start with Calc. This is the one I use the most.

---

### Post by jrog on 2012-10-16
> **mmasroorali said:**
> I was hoping that the problem will be solved any day. However, with only three days left before the final release, I thought that I must report the problem.
Thanks. You should probably also do this on official bug report channels, e.g.: [https://bugs.launchpad.net/ubuntu/+source/libreoffice](https://bugs.launchpad.net/ubuntu/+source/libreoffice)

Some of the things you mentioned (your #1, for example) have been reported as bugs there already, I think.

---

### Post by balloons on 2012-10-16
Possibly this bug? It's a known issue, but is likely to be SRU'd at this point.

[https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/1062068](https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/1062068)

---

### Post by jrog on 2012-10-16
> **guitara said:**
> Possibly this bug? It's a known issue, but is likely to be SRU'd at this point.

[https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/1062068](https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/1062068)
?

---

### Post by jerrylamos on 2012-10-16
> **dino99 said:**
> some questions:
- 32 or 64 bits install ?
- which DE : unity, GS, GC ?

here i have no issue with i386 on GCLatest RC updated on both 32 on my tower and 64 on my notebook the "File Edit View ...." are very flaky.  In particular, select an odt file to open LibreOffice Writer automatically has no "File Edit View ...".  Stumbled on a partial fix, do Alt-Tab to switch to other windows and back again, sometimes the "File ... etc" do appear on mouse over.  Launchpad bug #1067143

---

### Post by avinas on 2012-10-17
Same there.
Unity, 64 bit.
Even more - LibreOffice often is crashing my desktop completely. Dark screen and no reaction to anything only to hard/soft restarting is helping.

---

