---
title: "Problem installing ACROREAD via Multiverse"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by fantab on 2012-04-02
I am trying to** install ACROREAD on my 12.04_amd64** through Multiverse but I am unable to. I tried installing with Software Centre, which tells me to check my Internet Connection. 

But when I try to install it using Synaptic I get:

> **Could not mark all packages for installation or upgrade**
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences. 
acroread:
 Depends: ia32-libs but it is not going to be installedI have successfully installed Adobe Reader directly from Adobe.com but here I don't get the Mozilla-Plugin. I also installed nspluginwrapper. But it doesn't help. I thought may be installing it from Multiverse will help but... 

**I am unable to open PDFs in the Firefox. This is my real issue.**

Any help is appreciated.

Thanks...

---

### Post by philinux on 2012-04-02
Normally that comes from the partner repo. You may have to change the partner source to oneiric.

---

### Post by fantab on 2012-04-02
> **philinux said:**
> Normally that comes from the partner repo. You may have to change the partner source to oneiric.

That does not help either. I get same 'errors' even after changing and updating PARTNER repos to oneiric. 

I was wondering, isn't there any alternative to view PDFs in the browser?

---

### Post by santosh83 on 2012-04-02
> **fantab said:**
> That does not help either. I get same 'errors' even after changing and updating PARTNER repos to oneiric. 

I was wondering, isn't there any alternative to view PDFs in the browser?

 Chrome is an alternative which comes bundled with a PDF viewer. Also see: [https://support.mozilla.org/en-US/kb/Opening%20PDF%20files%20within%20Firefox](https://support.mozilla.org/en-US/kb/Opening%20PDF%20files%20within%20Firefox)

---

### Post by fantab on 2012-04-02
> **santosh83 said:**
> Chrome is an alternative which comes bundled with a PDF viewer. Also see: [https://support.mozilla.org/en-US/kb/Opening%20PDF%20files%20within%20Firefox](https://support.mozilla.org/en-US/kb/Opening%20PDF%20files%20within%20Firefox)

Thanks Santosh83,

But I avoid GOOGLE as best I can. 
Moreover I can open PDF in the Application but I want to open them in the FIREFOX BROWSER TABS....

---

### Post by philinux on 2012-04-02
> **fantab said:**
> That does not help either. I get same 'errors' even after changing and updating PARTNER repos to oneiric. 

I was wondering, isn't there any alternative to view PDFs in the browser?

I use acroread for the FF plugin too. I'll check this when I get home.

---

### Post by santosh83 on 2012-04-02
> **fantab said:**
> Thanks Santosh83,

But I avoid GOOGLE as best I can. 
Moreover I can open PDF in the Application but I want to open them in the FIREFOX BROWSER TABS....

There doesn't seem to be any other PDF viewer plugin for Firefox under Linux, other than Adobe's. :-(

Here're a couple flaky-looking work-arounds. One old plugin which claims to convert PDF to html on the fly, another Java applet based PDF viewer.
[http://www.gnostice.com/nl_article.asp?id=195&t=A_Java_PDF_Web_Viewer_-_Powered_By_PDFOne_%28for_Java%99%29]("http://www.gnostice.com/nl_article.asp?id=195&t=A_Java_PDF_Web_Viewer_-_Powered_By_PDFOne_%28for_Java%99%29#Notes")
[https://addons.mozilla.org/en-US/firefox/addon/pdf-download/](https://addons.mozilla.org/en-US/firefox/addon/pdf-download/)

---

### Post by gordintoronto on 2012-04-02
I installed Acroread in the 12.04 beta 2 with no problems. Perhaps you just need to try again.

---

### Post by cariboo on 2012-04-02
If worse comes to worse, you can always manually download acroread from here:

[http://archive.canonical.com/ubuntu/pool/partner/a/](http://archive.canonical.com/ubuntu/pool/partner/a/)

and then use dpkg, gdebi or the software centre to install it.

---

### Post by fantab on 2012-04-02
> **gordintoronto said:**
> I installed Acroread in the 12.04 beta 2 with no problems. Perhaps you just need to try again.

I tried again..... and it worked. I have installed Acroread from terminal. However it still does not work in FF Browser.

about: plugins

> **Adobe Reader 9.4**

 File:  npwrapper.nppdf.soVersion:   The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.    MIME Type Description Suffixes    application/pdf Portable Document Format pdf   application/vnd.fdf Acrobat Forms Data Format fdf   application/vnd.adobe.xfdf XML Version of Acrobat Forms Data Format xfdf   application/vnd.adobe.xdp+xml Acrobat XML Data Package xdp   application/vnd.adobe.xfd+xml Adobe FormFlow99 Data File xfdWhen I try to open any PDF in Browser I am asked to choose an "OPEN WITH" and when I choose Adobe Reader 9, it opens with the Application and not within Browser.

---

### Post by philinux on 2012-04-03
Sheesh.

Need to get 141 MB of archives.
After this operation, 400 MB of additional disk space will be used. It was in partner too.

I installed it to test. I forgot how many dependencies there are.

Opened a site that has a pdf part. Adobe licence popped up and accepted. FF plugin working fine.

---

### Post by compuguy1088 on 2012-04-03
Sounds like your having the same issue that this person has: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/970724](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/970724)

---

### Post by cariboo on 2012-04-03
Even the 64-bit version of acroread is a kludge of the 32-bit version, that depends on 32-bit libraries.

---

### Post by fantab on 2012-04-03
The adobe reader plugin is installed in the browser... but when I try to view any PDF the browser opens Adobe Reader instead. The plugin is still not working.

EDIT: I deleted dotmozilla folder. Then updated as there were updates for Firefox... Nothing still can't open PDF in the Browser. 

Can you suggest a test site from where PDF have opened for you in the FF browser? I want to check if there is any problem with the site I am using to open PDF.

@MODS: Please change the title of the thread to read "**Problem opening PDF in Browser with ACROREAD plugin**". Thanks

---

### Post by fantab on 2012-04-05
I have removed and reinstalled Acroread.

Three things happen when I try to open PDF in Firefox [FF] from various websites:

[LIST=1]
[*]PDF opens in the browser.
[*]PDF seems to open but the FF tab stays blank.
[*]PDF does not open in the FF but instead FF prompts to open the PDF with default application, Acroread.
[/LIST]
I cross checked the same in Windows using FF and adobe PDF plugin and all the PDFs open without any issues. 

I guess there is only so much I can do using LINUX... I am actually surprised and disappointed at the same time that there is no PDF extension or plugin for Firefox to be used with Linux. ](*,)

I wish and hope we (Linux users) will soon have a reliable PDF plugin for Firefox to view PDFs. 



If any of you guys have any practical solutions please post. 


Thanks...

---

### Post by shuttleworthwannabe on 2012-04-05
Have you checked in Adobe Reader preferences>internet that it is checked to open pdf in browser?? just a hunch; check if this works. Screenshot is from windows BTW to illustrate the point

---

### Post by philinux on 2012-04-05
> **fantab said:**
> I have removed and reinstalled Acroread.

Three things happen when I try to open PDF in Firefox [FF] from various websites:

[LIST=1]
[*]PDF opens in the browser.
[*]PDF seems to open but the FF tab stays blank.
[*]PDF does not open in the FF but instead FF prompts to open the PDF with default application, Acroread.
[/LIST]
I cross checked the same in Windows using FF and adobe PDF plugin and all the PDFs open without any issues. 

I guess there is only so much I can do using LINUX... I am actually surprised and disappointed at the same time that there is no PDF extension or plugin for Firefox to be used with Linux. ](*,)

I wish and hope we (Linux users) will soon have a reliable PDF plugin for Firefox to view PDFs. 



If any of you guys have any practical solutions please post. 


Thanks...

Strange indeed as it's working fine here. I wonder if you have an addon or even theme that's conflicting?

---

### Post by andrew.46 on 2012-04-05
> **santosh83 said:**
> There doesn't seem to be any other PDF viewer plugin for Firefox under Linux, other than Adobe's. :-(

Plugin perhaps but I quite happily open pdfs from Firefox in xpdf. Does not open in the browser window but I also don't have to run the bloated Acrobat behemoth :).

---

### Post by santosh83 on 2012-04-06
> **andrew.46 said:**
> Plugin perhaps but I quite happily open pdfs from Firefox in xpdf. Does not open in the browser window but I also don't have to run the bloated Acrobat behemoth :).

Indeed! After using Acrobat under Windows long ago (even then it was among the most bloated and slowest starting program), I've never considered it for Linux. I don't need the 'advanced' capabilities that Acrobat might provide, and happily use the default Evince, though now I'm intrigued enough to install and try xpdf, epdfview and other lightweight ones as well. :-)

---

### Post by andrew.46 on 2012-04-06
There is a nice closed source application called Foxit which is worth a look:

Foxit Reader
[http://www.foxitsoftware.com/Secure_PDF_Reader/](http://www.foxitsoftware.com/Secure_PDF_Reader/)

It is very nimble and looks good. On the downside there is the closed source thing, runs on 32bit only and there is an annoying advertisement. Myself, I will stick with xpdf but I dabbled with Foxit for a while :).

---

### Post by santosh83 on 2012-04-06
> **andrew.46 said:**
> There is a nice closed source application called Foxit which is worth a look:

Foxit Reader
[http://www.foxitsoftware.com/Secure_PDF_Reader/](http://www.foxitsoftware.com/Secure_PDF_Reader/)

It is very nimble and looks good. On the downside there is the closed source thing, runs on 32bit only and there is an annoying advertisement. Myself, I will stick with xpdf but I dabbled with Foxit for a while :).

Yes Foxit was my first choice replacement for Acrobat when I used Windows! Great to see it's now available for Linux; last time I looked it wasn't! Thanks :-)

---

### Post by andrew.46 on 2012-04-06
> **santosh83 said:**
> Yes Foxit was my first choice replacement for Acrobat when I used Windows! Great to see it's now available for Linux; last time I looked it wasn't! Thanks :-)

Looks like 32bit users can install it easily enough, as I demonstrate with the following *single* command:

```

wget http://cdn04.foxitsoftware.com/pub/foxit/reader/desktop/linux/1.x/1.1/enu/FoxitReader_1.1.0_i386.deb && \
sudo dpkg -i FoxitReader_1.1.0_i386.deb

```

64bit users may have to make other arrangements :)

---

### Post by philinux on 2012-04-06
> **andrew.46 said:**
> 
64bit users may have to make other arrangements :)

I'm on 64 bit and prefer acroread which is what this thread is about.. The arrangement I made was to enable Partner repo and use Software Centre.

---

### Post by santosh83 on 2012-04-06
> **andrew.46 said:**
> Looks like 32bit users can install it easily enough, as I demonstrate with the following *single* command:

```

wget http://cdn04.foxitsoftware.com/pub/foxit/reader/desktop/linux/1.x/1.1/enu/FoxitReader_1.1.0_i386.deb && \
sudo dpkg -i FoxitReader_1.1.0_i386.deb

```64bit users may have to make other arrangements :)

I'm guessing Precise 64-bit'ers needn't make any special arrangements and simply go ahead and give those commands, as multiarch support *should* take care of it! :-)

---

### Post by philinux on 2012-04-06
Evince is quite good now but no FF plugin as yet which is a shame.

It also fails to open complex pdf's that acroread can.

---

