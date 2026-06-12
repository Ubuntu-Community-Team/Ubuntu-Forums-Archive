---
title: "apache2 and microsoft publisher"
date: 2008-03-16
forum: Server Platforms
---

### Post by gishaust on 2008-03-16
Hi everyone,

I have a friend that wants to use my home web server for his own web page. We placed his webpage on the server and it will not work. I access the page but it will not work. The webpage was designed mirosoft publisher and if I look at the source code it make no sense to me here is an example.

```

<html xmlns:v="urn:schemas-microsoft-com:vml"
xmlns:o="urn:schemas-microsoft-com:office:office"
xmlns:dt="uuid:C2F41010-65B3-11d1-A29F-00AA00C14882"
xmlns:b="urn:schemas-microsoft-com:office:publisher"
xmlns="http://www.w3.org/TR/REC-html40">

<head>
<meta http-equiv=Content-Type content="text/html; charset=windows-1252">
<meta name=ProgId content=Publisher.Document>
<meta name=Generator content="Microsoft Publisher 11">
<link rel=File-List href="index_files/filelist.xml">
<!--[if !mso]>
<style>
v\:* {behavior:url(#default#VML);}
o\:* {behavior:url(#default#VML);}
b\:* {behavior:url(#default#VML);}
.shape {behavior:url(#default#VML);}
</style>
<![endif]--><!--[if gte mso 9]><xml>
 <o:DocumentProperties>
  <o:Author>Sam Stravakos</o:Author>
  <o:Version>11.5606</o:Version>
 </o:DocumentProperties>
</xml><![endif]--><!--[if pub]><xml>
 <b:Publication type="OplPub" oty="68" oh="256">
  <b:OhPrintBlock priv="30E">285</b:OhPrintBlock>
  <b:FWebPublication priv="C00">True</b:FWebPublication>
  <b:FWizardPub priv="E00">True</b:FWizardPub>
  <b:LoPageLayout priv="1104">11</b:LoPageLayout>
  <b:DptlPageDimensions type="OplPt" priv="1211">
   <b:Xl priv="104">7239000</b:Xl>
   <b:Yl priv="204">43891200</b:Yl>
  </b:DptlPageDimensions>

```


can anyone give me some direction

---

### Post by freebeer on 2008-03-17
It'd say it's Publisher and probably the expectation that whatever web code it generates assumes Microsoft's particular flavor of web server.  Publisher isn't (to my knowledge) primarily intended as a web development tool.  Basically he's using the wrong tool.  He should try maybe a Windows version of a real web development tool.

---

