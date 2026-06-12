---
title: "Easy OCR with ImageMagick and Tesseract-OCR"
date: 2010-01-02
forum: Tutorials
---

### Post by ALIENDUDE5300 on 2010-01-02
After playing with tesseract OCR for a while, I decided to write a simple bash script to automatically convert an image to a grayscale tif file and then run tesseract on it to convert the image to text. In case this is useful to anyone, I decided to share the source code for the script.

First, you need to make sure you have some packages installed, so type ```
sudo apt-get install imagemagick libpng12-dev libjpeg62-dev libtiff4-dev tesseract\*
```

Now, tesseract works much better when the source image is in grayscale, but most of the time it isn't, so this script uses the imagemagick convert tool to change the colorspace to Gray and convert the image to tif format. When using the script, which I will assume you saved as ocr.sh, you simply need to type ./ocr.sh imagename.png, replacing imagename with the name of the image. This script is fairly simple. It will save the output of the conversion as the filename of the original image with .txt appended to the end, and it uses ocr.tif as a temporary file for use with tesseract. Before you can run the script, make sure to type "chmod +x ocr.sh". This will set the executable bit on the file.

Here is the code of the bash script:
```
convert $1 -colorspace Gray ocr.tif 
tesseract ocr.tif $1
gedit $1.txt
```

---

### Post by nalin4linux77 on 2010-05-29
sir 
      we have tested your ocr soluution, but we find it a bit difficult to get continuous output. please 
test following link for an easy ocr solution  for ubuntu 10.04 
[http://code.google.com/p/easy-ocr/](http://code.google.com/p/easy-ocr/)

---

### Post by BoneKracker on 2010-05-29
Does "easyocr" use the tesseract engine.

I've never used easyocr, but in other tests I've done, I found nothing comes close to the accuracy of the awesome tesseract engine.  What engines do your product use?  How close can they come to tesseract's level of performance (and don't tell me they're "99% accurate", which is what everybody says about every engine out there, including the sucky ones).

---

### Post by Dayofswords on 2010-05-29
i tried the guide and made a test image:
[http://dayofswords.com/images/other/random/testocr.png](http://dayofswords.com/images/other/random/testocr.png)
with 'Sans' font on gimp with font sizes of 48, 40, 32, 24

but after running the script, it had an output of nothing, nothing was read.

i tested a screenshot of just my desktop and it read some parts, so it ran as it should...

---

### Post by nalin4linux77 on 2010-05-30
sir 
i send hear the test out put of the png file 

Loram ipsum dolor sit amat, consactatur adipisicing alit, sad do aiusmod  tampor
incididunt ut labora at dolora magna aliqua. Ut anim ad minim vaniam,  quis
nostrud axarcitation ullamco Iaboris nisi ut aliquip ax aa commodo  consaquat.
Duis auta irura dolor in raprahandarit in voluptata valit assa cillum  dolora au
fugiat nulla p8i‘l8‘EUi'. Excaptaur sint occaacat cupidatat non  proidant, sunt
in culpa qui officia dasarunt mollit anim id ast Iaborum. Loram ipsum  dolor sit
amat, consactatur adipisicing alit, sad do aiusmod tampor incididunt ut  Iabora
at dolora magna aliqua. Ut anim ad minim vaniam, quis nostrud  axarcitation
ullamco Iaboris nisi ut aliquip ax aa commodo consaquat. Duis auta irura  dolor
in raprahandarit in voluptata valit assa cillum dolora au fugiat nulla
pariatur. Excaptaur sint occaacat cupidatat non proidant, sunt in culpa  qui
officia dasarunt mollit anim id ast Iaborum. Loram ipsum dolor sit amat,
consactatur adipisicing alit, sad do aiusmod tampor incididunt ut Iabora  at
dolora magna aliqua. Ut anim ad minim vaniam, quis nostrud axarcitation  ullamco
Iaboris nisi ut aliquip ax aa commodo consaquat. Duis auta irura dolor  in
raprahandarit in voluptata valit assa cillum dolora au fugiat nulla  pariatur.
Excaptaur sint occaacat cupidatat non proidant, sunt in culpa qui  officia
dasarunt mollit anim id ast Iaborum. Loram ipsum dolor sit amat,  consactatur
adipisicing alit, sad do aiusmod tampor incididunt ut Iabora at dolora  magna
aliqua. Ut anim ad minim vaniam, quis nostrud axarcitation ullamco  Iaboris nisi
ut aliquip ax aa commodo consaquat. Duis auta irura dolor in  raprahandarit in
voluptata valit assa cillum dolora au fugiat nulla pariatur. Excaptaur  sint
occaacat cupidatat non proidant, sunt in culpa qui officia dasarunt  mollit anim
id ast Iaborum:KS

first i change the name of the png to 1.png, then paste it to  /home/username/OCR
(xsane automatically save hear ) then 
i have test it with two engines by pressing super+F1 and Super+F2 first  engine
and the second engine. engine two in which i have used tesseract   (super+F2,then super+F9 )
work well on this png.

first engine skipped it because of language problem we will fix it by  adding Language Pack :razz:
please test tool again and report :guitar:

---

### Post by MetaMs on 2010-07-22
> **nalin4linux77 said:**
> sir 
      we have tested your ocr soluution, but we find it a bit difficult to get continuous output. please 
test following link for an easy ocr solution  for ubuntu 10.04 
[http://code.google.com/p/easy-ocr/](http://code.google.com/p/easy-ocr/)

I have to comment on this post. I started using Ubuntu several months ago, and was very disappointed with the lack of a GUI OCR package. Being a newB and a non-code type of soul, I was forced back to windows using I.R.I.S. OCR (a very old version that I've owned for several years).

I was delighted to find the above post, and was able to install and use easy-ocr with no problems. The installation and use instructions could be clearer (more detail), but once you have it set up it works as promised. 

The accuracy rate is excellent. It's probably 10 times more accurate than my old I.R.I.S. software. So...thanks for a great program!

---

### Post by Copperblade on 2010-08-21
Thanks ALIENDUDE5300.

Here's my version of the script that is working for me on my PDF's (with multiple pages).

```

#!/bin/bash

tempdir="tmp"
outdir="ocr"

convert "$1" -colorspace Gray -depth 8 -resample 200x200 -verbose $tempdir/"$(echo $1| cut -d . -f1)_%04d.tif"

ls $tempdir | sort | xargs -i -t -P 2 tesseract $tempdir/"{}" $outdir/"$(echo {}| cut -d . -f1)"

exit 0

```

I tried using resolutions like 600x600, but I think it crashes out of memory.  Maybe `gs` would be a better tool to use than `convert` for this.

Also tesseract seems to bail if:

[LIST]
[*]The depth is higher than 8 bpp
[*]The file ends with .tiff instead of .tif
[/LIST]

By the way, this script takes quite some time to do its work.  You can try getting rid of the -resample argument completely, but I haven't tried it without it.  You might need to do that anyway if you're running out of memory (I seem to maxing out 2GB with this).

---

### Post by craq on 2011-07-17
after playing with this and some other solutions I got from

[https://help.ubuntu.com/community/OCR](https://help.ubuntu.com/community/OCR)
[http://sourceforge.net/projects/tesseract-ocr/forums/forum/534361/topic/1568751](http://sourceforge.net/projects/tesseract-ocr/forums/forum/534361/topic/1568751)
[http://www.unix.com/shell-programming-scripting/55661-how-get-number-pages-pdf-file-2.html](http://www.unix.com/shell-programming-scripting/55661-how-get-number-pages-pdf-file-2.html)

I came up with this, which seems to be working robustly for me:
```
#!/bin/bash

DELT=TRUE
DELG=TRUE
TARGETDIR=/tmp/
OUTPUT=/tmp/

if [[ -z "$1" ]]
then
echo "Usage: $0 files_to_OCR
Examples:
$0 file1 file2 ...
scans the files and saves all the text to similarly named .txt files.
A log is saved to tes.error.log
"

exit
fi
# redirect error to log.file and fd 5 to stout
# is changed in -f or -s
exec 2>tes.error.log
exec 5>&1




for i in $*
do
I_FILE=${i##.*/} #just the filename w/o directory
if [[ ! -f "$i" ]]
then
echo "$i: file not found" >&2
else
if ! identify "$i" 2>/dev/null 1>&2 # check if graphics file can be converted
then
echo "$i: not convertable" >&2
else
echo "processing: $i ..." >&2
# converting the graphic file

#get number of pages and perform conversion one page at a time
#added cjr 20110717
PAGES=$( pdfinfo $i | grep 'Pages' - | awk '{print $2}' )
OUTPUT=$(echo $i| cut -d . -f1).txt

for j in `seq 1 $PAGES`; do
	convert -monochrome -density 600 $i\[$(($j - 1 ))\] page$j.tif
	tesseract page$j.tif page$j
	if [ $j -eq 1 ]
	then
		cat page$j.txt > temp.txt
	else
		cat $OUTPUT page$j.txt > temp.txt
	        rm $OUTPUT
	fi
	rm page$j.tif
	rm page$j.txt
	mv temp.txt $OUTPUT
done

echo $i completed

fi

fi
done
```

---

### Post by nalin4linux77 on 2012-02-27
[SIZE=4]_**Linux-intelligent-ocr-solution**_[/SIZE]

LIOS is a free and open source software for converting print in to text using either scanner or a camera. It can also produce text out of scanned images from other sources. Program is given total accessibility for visually impaired. LIOS is written in python and we release it under GPL3 license. LIOS will work with Debian based operating systems. LIOS is an effort from the easy-ocr development team. There are great many possibilities for this program. Feedback is the key to it. expecting your feedback. 
[U][B]
HOW TO INSTALL[/B][/U]

[B]Download deb file from here [http://linux-intelligent-ocr-solution.googlecode.com/](http://linux-intelligent-ocr-solution.googlecode.com/) download the latest deb package and install
What is new in LIOS-1.2
1 Cam-Scan,
2 Cam-Reader,
3 Scan-to-image-only,
4 Scan-to-images-repeatedly,
5 Introduction of py-sane, Glaid library make the program faster and efficient,
6 Multiple arguments are handled effectively,
7 Ocr a single Image,
8 Artha shortcut (alt+control+W),
9 Beta version of spell-checker,
10 Provision for submitting issues in the About Dialog.
Features
1 Single scan & Repeated Scanning,
2 Ocr Folder,
3 Ocr Pdf,
4 Ocr image only,
5 Cam-Scan and Cam-Reader,
6 Scan-for-image-only & repeatedly,
7 24 Language support (Given at the end),
8 Full GUI environment,
9 Selection of starting page number, page numbering mode and number of pages to scan,
10 Selection of Scan area, brightness, resolution and time between repeated scanning,
11 Full Auto Rotation,[/B]:lolflag:
[B] 12 Brightness optimizer,
13 Audio converter,
14 Easily Accessible Preferences Window,
15 5 OCR Engines (OCROPUS,CUNEIFORM,TESSERACT,GOCR,OCRAD),
16 Good text manipulation with Find, Go-To-Page, Go-To-Line, Append file, Punch File.
17 Display Preferences for Low vision,
18 Dictionary Support for English(Artha)
19 Beta version of spell-checker,
20 Provision for submitting issues,
21 And more features are in the preferences.[/B]
**How to start using LIOS.**:guitar:
1. Scanning.

In order to start new scan, first press ctrl+n and then press f9 for single scan or ctrl+f9 for repeated scanning. To set the scanning preferences press ctrl+p and set the starting page number, Mode of page numbering, double page mode if you intend to keep 2 pages at a time, rotation to select the way in which you want the program to rotate the images before conversion. In full automatic rotation mode, one can keep the book in 00 90 180 and 270 degree angle. In partial rotation mode program will scan once to find out the position of the book and then the rotation will be kept. In manual mode one should select the angle. partial and manual mode is faster than full auto rotation mode in ocr process. One can select the number of pages to be scanned at a stretch by setting number of pages in the case of repeated scanning. One can stop all scanning process by pressing ctrl f4.
2. Cam-scan.

one can now use Hovercam or a Webcam to produce text in LIOS. Adjustments with these devices can be made using LIOS-cam-preferences in edit menu. This feature will help to read books and other printed materials such as visiting cards currency and like and also it makes the ocr process very fast and accurate. Please be specific to use devices with auto focusing facility. remember that there is no autorotation in this utility.so for the same reason, support of a stand for the webcam will be highly appreciated.
3. Cam-reader.

is the utility which will give a continuous output as one moves the webcam. First it will create the image and then will produce the text and it will start reading. After the completion of reading, it will repeat the process automatically. In cam-scan, one has to take the photo and it will be converted in to text.
4. Ocr Image.

LIOS can convert image file to text which is in jpg, tif, png, pnm and bmp.
5. Ocr folder.

LIOS can convert scanned images from other sources. It can convert jpg, jpeg, tif, tiff png, pnm, formats. To convert the images in a folder, select scan from folder option from scan menu and then select the input folder.
6. Ocr Pdf file.

Select Ocr pdf from scan menu and then select the input file. It is recommended that one can use ocropus as engine more efficiently in pdf conversion.
7. scan for image only and scan for images only repeatedly.

Help one to scan only images and it will give the user opportunity to utilize different ocr engines conveniently. Also it avoids delay between each scan if one does not want to listen to the output. Images will be saved in LIOS or one can choose his own destination. Now conversion can be done using folder option.
8. Brightness checker.

To set a n exact value of brightness or threshold is the best way to ensure maximum efficiency out of ocr engines. To find out the best value, go to tools menu and select brightness checker. This utility will scan for 15 or 17 times to complete the process. After the process, number of words detected at different values will be shone in tabs. If you want to know the precise value only, shift tab and then tab to apply the value.
9. Audio conversion.

LIOS can convert the text opened in LIOS to wav files. To convert the text in to speech, go to tools menu and select audio converter.
10. Text Manipulation.

To go to page, press ctrl+g and then type the page number, and tab to OK. In the case of double page type only odd number, for example 1 in the case of 1-2 and 11 in the case of 11-12. One can go to any line by pressing ctrl+l and ctrl+f will help to find any word in the document.
11. Display preferences.

display preferences in the edit menu will help to set fond size, color , italic, bold and color of the background.
12. Engines.

There are 5 engines in LIOS.out of these only cuneiform can handle 24 languages, list given at the end. All other engines can handle only English. Cuneiform is good for speed and picture skipping ,ocropus is good for layout analysis and pdf conversion.
13. Artha.

In order to find out the meaning of English words, first select the word and then press alt+ctrl+w and tab to find the meaning. Caution for the first time one has to press alt+control+w twice so as to switch on artha
14. Spell checker.

A beta version of spell checker is added to the program.press ctrl f7 and all the misspelled words will appear and one can change them.
Cuneiform support Bulgarian, Croatian, Czech, Danish, Dutch, English, Estonian, French, German, Hungarian, Italian, Latvian, Lithuanian, Polish, Portuguese, Romanian, Russian, Russian-English bilingual, Serbian, Slovene, Spanish, Swedish, Turkish, and Ukrainian.
**Disclaimer**

    Copyright (c) 2011-2012 LIOS Development Team 

    All rights reserved . Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met: 

    Redistributions of source code must retain the below copyright notice, 

    this list of conditions and the following disclaimer. 

    Redistributions in binary form must reproduce the below copyright notice, 

    this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution. 

    Neither the name of the nor the easyocr team names of its 

    contributors may be used to endorse or promote products derived from this software without specific prior written permission. 

    THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE." 

**FREE SOFTWARE FREE SOCIETY**:lolflag:

---

### Post by oldos2er on 2012-02-27
Closed, necromancy.

---

