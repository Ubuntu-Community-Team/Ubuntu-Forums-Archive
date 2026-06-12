---
title: "MS Word free batch converters"
date: 2008-02-08
forum: The Cafe
---

### Post by BDNiner on 2008-02-08
I was wondering if there was any free software that will convert a batch of word documents to templates? I was given a couple hundred word docs at work and they want them converted to templates and i am not going to do it one by one. I have only been able to find paid software when i searched google.

Any help?

---

### Post by dca on 2008-02-08
Unfortunately if it's going to run on Windows (third party proprietary apps) it's gonna' cost money.  If it's a real good program (ie:  something that can batch print many multi-page files at once) not only do you pay for it up front, you pay a yearly maintenance fee on it...  Sorry...

---

### Post by koenn on 2008-02-08
I don't know about any existing tools for this, but it's quite an easy task to do in vb script :
if you create a Word Application object, you have access to Word's FileOpen and SaveAs methods, So you can iterate through your files, open them, get their name from the Name property, and use SaveAs to save them as a template (and reuse the name).
it's going to be about 10-15 lines of code. If you don't know vbscript, try searching for one or try your luck at vbscripters sites and forums.

---

### Post by BDNiner on 2008-02-08
Thanks koenn, i will look into that this weekend. I don't want to come into work but i want to convert all my pictures to digital form so that would give me a worth while reason to come into work and use the scanner. and while i am at it convert all the word documents.

---

### Post by koenn on 2008-02-09
I had some time to kill and it looked like an interesting exercise so I gave it a try myself. 
It feels strange to post vb script to do ms-word stuff on a Linux forum, but here you go :

```

' batch convert MS WORD documents to a different (msword) file format
' see also http://www.robvanderwoude.com/vbstech_automation_word.html

'
strSRC="D:\testfiles\docs" 		'where are the files to be converted
strTARGET="D:\testfiles\templates" 	'directory where you want to put the result
'' we assume these folders exist !!

Const wdFormatTemplate =  1


'create objects you'll need
set fso = Wscript.CreateObject("scripting.FileSystemObject")
set oWord = Wscript.CreateObject( "Word.Application")

'get SRC folder and files therein
set oSrcFolder = fso.GetFolder(strSRC)
set colFiles = oSrcFolder.Files

'iterate and convert
With oWord
	.Visible = True			'or False
	For each oFile in colFiles
		strNewName = fso.BuildPath( strTARGET, fso.GetBaseName( oFile ) & ".dot" )
		.Documents.Open oFile.Path 
		set oDoc = .ActiveDocument
		oDoc.SaveAs strNewName, wdFormatTemplate 
		oDoc.CLose

	Next 'file
	.Quit 'MS_Word
End With

'clean exit

set oSrcFolder = Nothing
set colFiles = Nothing
set fso = Nothing
set oWord = Nothing
wscript.quit

```

---

