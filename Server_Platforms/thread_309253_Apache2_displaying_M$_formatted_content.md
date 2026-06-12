---
title: "Apache2 displaying M$ formatted content"
date: 2006-11-29
forum: Server Platforms
---

### Post by Hotei on 2006-11-29
I have searched all over and I must not be able to come up with the correct search words or something. Here is the deal...

I have a Debian 3.1 sarge system running Apache2. We receive and obscene amount of material from our customers formated in M$ Word or Excel format that individuals here just throw up on the web. On the Debian system these pages come up with no troubles at all.

Problem is that the decision has been made to move every one of our Linux servers to Ubuntu . I have setup the new system the same but instead of displaying the M$ formated pages correctly, it is interpreting the 'special M$ formatting' as wing-dings...

Example:
1) What are the Pricing subsegments for:&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; ESR&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; Non-ESR&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;

Now the black boxes should just be an underline for the answer (this is a printable test...) I am getting this all over the place and I can't seem to figure it out. I have checked to make sure the same modules are installed and working, the config files and the same (pulled the working ones from the server that displaying them correctly) and I just can't seem to put my finger on the what is going on.

Any help or suggestions would be appreciated.

Thank you.

---

### Post by MJN on 2006-11-29
What format are the pages in? Word/Excel binary docs or HTML files? If the latter, what encoding are they in (i.e. what's the **<charset=** settings in the <HEAD> section)?

If there's none set it may be falling back on the default Apache setting (which I don't recall at the moment) but you can set it with **AddDefaultCharset**.

However, if they're not HTML pages then this of course is not going to help...

Mathew

---

### Post by Hotei on 2006-11-30
MJN thank you for your reply.

Here is what the file header looks like and the display I included in the initial message:

<html xmlns:o="urn:schemas-microsoft-com:office:office"
xmlns:w="urn:schemas-microsoft-com:office:word"
xmlns="http://www.w3.org/TR/REC-html40">

<head>
<meta http-equiv=Content-Type content="text/html; charset=windows-1252">
<meta name=ProgId content=Word.Document>
<meta name=Generator content="Microsoft Word 9">
<meta name=Originator content="Microsoft Word 9">
<link rel=File-List href="./quiz6.21.01_files/filelist.xml">
<title>Client Worksheet/Quiz</title>
<!--[if gte mso 9]><xml>
 <o:DocumentProperties>
  <o:Author>Author1</o:Author>
  <o:Template>Normal</o:Template>
  <o:LastAuthor>Author2</o:LastAuthor>
  <o:Revision>2</o:Revision>
  <o:TotalTime>10</o:TotalTime>
  <o:LastPrinted>2001-02-22T13:34:00Z</o:LastPrinted>
  <o:Created>2001-06-21T17:24:00Z</o:Created>
  <o:LastSaved>2001-06-21T17:24:00Z</o:LastSaved>
  <o:Pages>1</o:Pages>
  <o:Words>410</o:Words>
  <o:Characters>2341</o:Characters>
  <o:Company>Company</o:Company>
  <o:Lines>19</o:Lines>
  <o:Paragraphs>4</o:Paragraphs>
  <o:CharactersWithSpaces>2874</o:CharactersWithSpaces>
  <o:Version>9.3821</o:Version>
 </o:DocumentProperties>
</xml><![endif]-->
<style>
<!--
 /* Font Definitions */
@font-face
        {font-family:Tahoma;
        panose-1:2 11 6 4 3 5 4 4 2 4;
        mso-font-charset:0;
        mso-generic-font-family:swiss;
        mso-font-pitch:variable;
        mso-font-signature:16792199 0 0 0 65791 0;}
 /* Style Definitions */
p.MsoNormal, li.MsoNormal, div.MsoNormal
        {mso-style-parent:"";
        margin:0in;
        margin-bottom:.0001pt;
        mso-pagination:widow-orphan;
        font-size:12.0pt;
        font-family:"Times New Roman";
        mso-fareast-font-family:"Times New Roman";}
h1
        {mso-style-next:Normal;
        margin:0in;
        margin-bottom:.0001pt;
        mso-pagination:widow-orphan;
        page-break-after:avoid;
        mso-outline-level:1;
        font-size:12.0pt;
        font-family:Arial;
        mso-font-kerning:0pt;}
@page Section1
        {size:8.5in 11.0in;
        margin:.25in .3in .3in .25in;
        mso-header-margin:.5in;
        mso-footer-margin:.5in;
        mso-paper-source:0;}
div.Section1
        {page:Section1;}
-->
</style>
</head>

<body lang=EN-US style='tab-interval:.5in' leftmargin="20">
<div class=Section1>

(part 1, said I had to many images...)

---

### Post by Hotei on 2006-11-30
(continued...)

 <p class=MsoNormal><span style='font-size:10.0pt;mso-bidi-font-size:12.0pt;
font-family:Tahoma'>1) What are the Pricing subsegments for:<span
style='mso-tab-count:1'>| | | | | |  </span>ESR<u><span style='mso-tab-count:1'>| | | | | 
    </span><span
style='mso-tab-count:2'>| | | | | | | | | | | | | | | | | | | | | | |  </span><o:p></o:p></u></span>&nbsp;&nbsp;&nbsp;<span style='font-size:10.0pt;mso-bidi-font-size:12.0pt;
font-family:Tahoma'>Non-ESR<u><span style='mso-tab-count:
2'>| | | | | | | | | | | | | | | | |  </span><o:p></o:p></u></span></p>

<p class=MsoNormal><span style='font-size:10.0pt;mso-bidi-font-size:12.0pt;
font-family:Tahoma'><![if !supportEmptyParas]>&nbsp;<![endif]><o:p></o:p></span></p>


Again, thank you for the reply.  I am still working on this and it is killing me because I want to move to Ubuntu, but as is now... this is kind of a deal breaker.  We have hundreds of pages that are being displayed like this.  I am hoping to find a server side solution.  I have been told that it isn't feasible to edit the hundreds of documents to make this work.

I have checked the difference between the environment settings of the servers.  I changed the LANG setting to match... no solution.  I am checking further against difference in packages, but I am leaning more toward an environment variable.  I don't know what to check on them both to compare them.  

Thanks in advance for your replies.

--Hotei

---

### Post by MJN on 2006-11-30
Okay, so they're HTML/XML documents (the 'Microsoft' element is just clouding the issue - they just happen to be using a 'rich' character set).

Which is a good thing... as Apache can ensure the correct character set is advised to the client using the **AddDefaultCharset** directive.

I'm no expert when it comes to character sets (so someone else step in with a more suitable set) however give **AddDefaultCharset ISO-8859-1** a try in apache2.conf then reload and recheck.... any difference?

Have you still got your Debian config files? If so, see if it has an AddDefaultCharset directive defined - it may well do. Alternatively, run a packet sniffer on a web access to the Debian server and see what character set is being returned to the client (and compare this with Ubuntu).

Mathew

---

### Post by Hotei on 2006-11-30
Thank you MJN.  I will give those a try.  Might take a bit to get the sniffer in place but it is something to try.  

Thanks again, I will post finds when I get them done.

---

### Post by MJN on 2006-11-30
Start with the AddDefaultCharset directive as mentioned - you might strike lucky.

Mathew

---

### Post by Hotei on 2006-12-07
MJN, can't thank you enough.  the AddDefaultCharset ISO-8859-1 did the trick.    Is there a reason why it is commented out by default in the apache2.conf file?  

Anyway, it is fixed and looking good.  Thanks again.

--Hotei

---

### Post by MJN on 2006-12-07
To keep you on your toes of course, and to make migrating from one distro to another full of surprises... ;) (how do you think I found it!)

Seriously, it was down to security issues that the otherwise-default AddDefaultCharset directive was removed as it could give rise to variations of the potential for a mailicous page encoded in one character set, yet not specified in the META tags, to be delivered by the server as a page encoded as another character set - this could possibly lead to malicious scripts passing through undetected.

Of course, if you've got control of your server pages then this isn't an issue for you so the directive now included is quite safe.

Mathew

---

