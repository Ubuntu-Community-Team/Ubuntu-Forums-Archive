---
title: "The perfect Linux OCR and PDF solution - 95% (we can do it!)"
date: 2012-02-17
forum: Server Platforms
---

### Post by sirsiwsh on 2012-02-17
[SIZE=2][COLOR=#000000][FONT=Tahoma]Hi all,[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[/SIZE] [SIZE=2][COLOR=#000000][FONT=Tahoma]I'm in the process of setting up a kick-*** server (and am frustratingly close to the finish line!)- one of the things I'd like it to be able to do is scan in documents and automatically OCR them, so that at the end I'm left with a searchable PDF of whatever it was I scanned in.[/FONT][/COLOR]
[/SIZE] [SIZE=2][COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[/SIZE] [SIZE=2][COLOR=#000000][FONT=Tahoma]I've already managed to automate the scanning process, so the machine will scan to PDF and archive it already. I can OCR the text almost to 100% accuracy (tesseract is the winner here by far), and get layout pretty close, however when it comes to defining the layout in a PDF I'm getting stuck.[/FONT][/COLOR]
[/SIZE] [SIZE=2][COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[/SIZE] [SIZE=2][COLOR=#000000][FONT=Tahoma]I've come across several options that supposedly allow me to do what I want- tesseract to hocr (very nearly perfect html layout!), ocropus via a layout plugin etc but none are very accurate when it comes to doing the layout. hocr2pdf, the frontrunner, succesfully puts the text in the right place but garbles it up- even with the "-s" (sloppy switch). This means the PDF isn't searchable properly. [/FONT][/COLOR]
[/SIZE] [SIZE=2][COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[/SIZE] [SIZE=2][COLOR=#000000][FONT=Tahoma]If you want to see what I mean, the various tests I've run so far can be seen below:[/FONT][/COLOR]
[/SIZE] [SIZE=2][COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]
[/SIZE] [SIZE=2][COLOR=#000000][FONT=Tahoma]Original Image: HTTP.jpg               [http://www.filefactory.com/file/c3a9343/n/HTTP.jpg](http://www.filefactory.com/file/c3a9343/n/HTTP.jpg)[/FONT][/COLOR]
[/SIZE] [SIZE=2]Unpapered: HTTP.unpaper.jpg        [http://www.filefactory.com/file/c3a9346/n/HTTP.unpaper.jpg](http://www.filefactory.com/file/c3a9346/n/HTTP.unpaper.jpg)   
[/SIZE] [SIZE=2]Converted: HTTP.unpaper.pbm        N/A 
[/SIZE] [SIZE=2]Tiff: HTTP.unpaper.tiff                    N/A
[/SIZE] [SIZE=2]

[/SIZE] [SIZE=2]All OCR was done on the HTTP.unpapered.pbm image.
[/SIZE] [SIZE=2]

[/SIZE] [SIZE=2]OCR Results:
[/SIZE] [SIZE=2]Engine                             File                     Result               View
[/SIZE] [SIZE=2]Tesseract HTML (HOCR)   HTTP.out.html      Excellent             [http://www.filefactory.com/file/c3a9385/n/HTTP.out.html](http://www.filefactory.com/file/c3a9385/n/HTTP.out.html)
[/SIZE] [SIZE=2]Tesseract TXT                 HTTP.out.txt        Excellent              [http://www.filefactory.com/file/c3a9352/n/HTTP.out.txt](http://www.filefactory.com/file/c3a9352/n/HTTP.out.txt)
[/SIZE] [SIZE=2]

[/SIZE] [SIZE=2]PDF Creation Results:
[/SIZE] [SIZE=2]Sample text output (copy/pasted from PDF- the same text you are searching through in the PDF document) can be found here: [http://pastebin.com/CZVqQtpS](http://pastebin.com/CZVqQtpS)
[/SIZE] [SIZE=2]

[/SIZE] [SIZE=2]Engine                              Result               View PDF                   
[/SIZE] [SIZE=2]hocr2pdf                           Poor                  [http://www.filefactory.com/file/c3a921a/n/hocr2pdf.pdf](http://www.filefactory.com/file/c3a921a/n/hocr2pdf.pdf)
[/SIZE] [SIZE=2]hocr2pdf sloppy                 Fair                   [http://www.filefactory.com/file/c3a9254/n/hocr2pdf_sloppy.pdf](http://www.filefactory.com/file/c3a9254/n/hocr2pdf_sloppy.pdf)
[/SIZE] [SIZE=2]gscan2pdf                         Excellent            [http://www.filefactory.com/file/c3a9203/n/gscan2pdf.pdf](http://www.filefactory.com/file/c3a9203/n/gscan2pdf.pdf)
[/SIZE] [SIZE=2]OCRFeeder                       Poor                  [http://www.filefactory.com/file/c3a926d/n/ocrfeeder.pdf](http://www.filefactory.com/file/c3a926d/n/ocrfeeder.pdf)
[/SIZE] [SIZE=2]hocr2pdf text only              Excellent            [http://www.filefactory.com/file/c3a926a/n/hocr2pdf_text_only.pdf](http://www.filefactory.com/file/c3a926a/n/hocr2pdf_text_only.pdf)
[/SIZE] [SIZE=2](hocr2pdf -i HTTP.unpaper.tiff -o HTTP-ocr.pdf < HTTP.out.txt)
[/SIZE] [SIZE=2]

[/SIZE] [SIZE=2]Notice hocr2pdf with the text only file (i.e only line breaks, no layout gives practically the same result as gscan2pdf, but the text is up in the top left corner!) I guess I'd be happy with the hocr2pdf text only version, but its not >95% accuracy, and it'd be nice to get the layout too...
[/SIZE] [SIZE=2]

[/SIZE] [SIZE=2]The best by far and away is gscan2pdf- it's almost 100% accurate and puts the text in the right place, and searching through the resulting PDF actually returns results, albeit with hilariously odd text sizes in the same sentence. BUT I can't use it over the command line. I've trawled through the code (perl, not my strong suit) and it appears there is a subroutine called boxes which works out the size and position of the text (x,y; x,y; text). The subroutine uses a html parser (HTML::TokeParser), so I guess it's not rocket science, but, please, does anyone know of anyway to get this exact functionality achieved over the command line?
[/SIZE] [SIZE=2]

[/SIZE] [SIZE=2]Alternatively, does anyone know of an equivalent quality hocr > pdf creator? If not, is anyone game to help me write a CLI equivalent?
[/SIZE] [SIZE=2]

[/SIZE] [SIZE=2]I'll be writing up HOWTOs (scripts and everything) when I'm done to give the love back to the community so please don't be afriad to pitch in or complain to the program creators, etc.
[/SIZE] [SIZE=2]

[/SIZE] [SIZE=2]Thanks!

**Apologies, it seems I can't tab or add in the HTML to make things tab properly!
[/SIZE]

---

