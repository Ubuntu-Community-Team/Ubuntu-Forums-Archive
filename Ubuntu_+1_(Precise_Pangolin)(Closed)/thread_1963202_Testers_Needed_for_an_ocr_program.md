---
title: "Testers Needed for an ocr program"
date: 2012-04-22
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by 3togo on 2012-04-22
Pls help me test the following ocr program in Precise Pangolin

1. ```
sudo apt-get install python-support libleptonica libopencv-core2.3 libwebp2 libtesseract3 tesseract-ocr tesseract-ocr-eng tesseract-ocr-osd tesseract-ocr-equ
```

2. Download and Install python-tesseract
```
wget http://python-tesseract.googlecode.com/files/python-tesseract_0.7-1.4_i386.deb

wget http://python-tesseract.googlecode.com/files/python-tesseract_0.7-1.4_amd64.deb

```
3. Download the image file used for ocr
```
wget http://python-tesseract.googlecode.com/files/eurotext.jpg

```
4. Test it by running the following python script
```
import tesseract
api = tesseract.TessBaseAPI()
api.Init(".","eng",tesseract.OEM_DEFAULT)
api.SetPageSegMode(tesseract.PSM_AUTO)

mImgFile = "eurotext.jpg"
mBuffer=open(mImgFile,"rb").read()
result = tesseract.ProcessPagesBuffer(mBuffer,len(mBuffer),api)
print "result(ProcessPagesBuffer)=",result

```

Many thanks

---

### Post by keithpeter on 2012-04-22
Hello 3togo

Below on a 12.04 installation updated to this morning
```

keith@xeon:~$ sudo dpkg -i python-tesseract_0.7-1.4_i386.deb
Selecting previously unselected package python-tesseract.
(Reading database ... 315579 files and directories currently installed.)
Unpacking python-tesseract (from python-tesseract_0.7-1.4_i386.deb) ...
dpkg: dependency problems prevent configuration of python-tesseract:
 python-tesseract depends on python-support (>= 0.90.0); however:
  Package python-support is not installed.
 python-tesseract depends on libleptonica; however:
  Package libleptonica is not installed.
 python-tesseract depends on libopencv-core2.3; however:
  Package libopencv-core2.3 is not installed.
 python-tesseract depends on libtesseract3; however:
  Package libtesseract3 is not installed.
 python-tesseract depends on tesseract-ocr; however:
  Package tesseract-ocr is not installed.
dpkg: error processing python-tesseract (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-tesseract
keith@xeon:~$ sudo apt-get install python-support libleptonica libopencv-core2.3 libtesseract3 tesseract-ocr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libleptonica : Depends: libwebp2 but it is not going to be installed
 tesseract-ocr : Depends: tesseract-ocr-eng (>= 3.01~) but it is not going to be installed
                 Depends: tesseract-ocr-osd but it is not going to be installed
                 Depends: tesseract-ocr-equ but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by i386DX on 2012-04-22
Here you are:

```

test@test-VirtualBox:~$ python test.py 
result(ProcessPagesBuffer)= The (quick) [brown] {fox} jumps!
Over the $43,456.78 <lazy> #90 dog
& duck/goose, as 12.5% of E-mail
from aspammer@website.com is spam.
Der ,,schnelle” braune Fuchs springt
&#64257;ber den faulen Hund. Le renard brun
«rapide» saute par-dessus le chien
paresseux. La volpe marrone rapida
salta sopra il cane pigro. El zorro
marrén répido salta sobre el perro
perezoso. A raposa marrom rzipida
salta sobre o c&#64257;o preguicoso.

```

---

### Post by 3togo on 2012-04-22
try

sudo apt-get -f install


> **keithpeter said:**
> Hello 3togo

Below on a 12.04 installation updated to this morning
```

keith@xeon:~$ sudo dpkg -i python-tesseract_0.7-1.4_i386.deb
Selecting previously unselected package python-tesseract.
(Reading database ... 315579 files and directories currently installed.)
Unpacking python-tesseract (from python-tesseract_0.7-1.4_i386.deb) ...
dpkg: dependency problems prevent configuration of python-tesseract:
 python-tesseract depends on python-support (>= 0.90.0); however:
  Package python-support is not installed.
 python-tesseract depends on libleptonica; however:
  Package libleptonica is not installed.
 python-tesseract depends on libopencv-core2.3; however:
  Package libopencv-core2.3 is not installed.
 python-tesseract depends on libtesseract3; however:
  Package libtesseract3 is not installed.
 python-tesseract depends on tesseract-ocr; however:
  Package tesseract-ocr is not installed.
dpkg: error processing python-tesseract (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-tesseract
keith@xeon:~$ sudo apt-get install python-support libleptonica libopencv-core2.3 libtesseract3 tesseract-ocr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 libleptonica : Depends: libwebp2 but it is not going to be installed
 tesseract-ocr : Depends: tesseract-ocr-eng (>= 3.01~) but it is not going to be installed
                 Depends: tesseract-ocr-osd but it is not going to be installed
                 Depends: tesseract-ocr-equ but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by 3togo on 2012-04-22
Many thanks  :)

> **i386DX said:**
> Here you are:

```

test@test-VirtualBox:~$ python test.py 
result(ProcessPagesBuffer)= The (quick) [brown] {fox} jumps!
Over the $43,456.78 <lazy> #90 dog
& duck/goose, as 12.5% of E-mail
from aspammer@website.com is spam.
Der ,,schnelle” braune Fuchs springt
&#64257;ber den faulen Hund. Le renard brun
«rapide» saute par-dessus le chien
paresseux. La volpe marrone rapida
salta sopra il cane pigro. El zorro
marrén répido salta sobre el perro
perezoso. A raposa marrom rzipida
salta sobre o c&#64257;o preguicoso.

```

---

### Post by abyrne on 2012-04-22
Fresh 12.04 install.
```

result(ProcessPagesBuffer)= The (quick) [brown] {fox} jumps!
Over the $43,456.78 <lazy> #90 dog
& duck/goose, as 12.5% of E-mail
from aspammer@website.com is spam.
Der ,,schnelle” braune Fuchs springt
&#64257;ber den faulen Hund. Le renard brun
«rapide» saute par-dessus le chien
paresseux. La volpe marrone rapida
salta sopra il cane pigro. El zorro
marrén répido salta sobre el perro
perezoso. A raposa marrom rzipida
salta sobre o c&#64257;o preguicoso.




```

---

### Post by keithpeter on 2012-04-22
> **3togo said:**
> try

sudo apt-get -f install

Hello 3togo

Yes, that worked.

```
keith@xeon:~$ python ocr.py
result(ProcessPagesBuffer)= The (quick) [brown] {fox} jumps!
Over the $43,456.78 <lazy> #90 dog
& duck/goose, as 12.5% of E-mail
from aspammer@website.com is spam.
Der ,,schnelle” braune Fuchs springt
&#64257;ber den faulen Hund. Le renard brun
«rapide» saute par-dessus le chien
paresseux. La volpe marrone rapida
salta sopra il cane pigro. El zorro
marrén répido salta sobre el perro
perezoso. A raposa marrom rzipida
salta sobre o c&#64257;o preguicoso.
```

---

### Post by Irihapeti on 2012-04-22
```
ja@ja-laptop:~$ python test.py
result(ProcessPagesBuffer)= The (quick) [brown] {fox} jumps!
Over the $43,456.78 <lazy> #90 dog
& duck/goose, as 12.5% of E-mail
from aspammer@website.com is spam.
Der ,,schnelle” braune Fuchs springt
&#64257;ber den faulen Hund. Le renard brun
«rapide» saute par-dessus le chien
paresseux. La volpe marrone rapida
salta sopra il cane pigro. El zorro
marrén répido salta sobre el perro
perezoso. A raposa marrom rzipida
salta sobre o c&#64257;o preguicoso.

```
Had to do the "apt-get -f install" thing, too, before it would install properly.

---

### Post by 3togo on 2012-04-22
Many thanks

> **abyrne said:**
> Fresh 12.04 install.
```

result(ProcessPagesBuffer)= The (quick) [brown] {fox} jumps!
Over the $43,456.78 <lazy> #90 dog
& duck/goose, as 12.5% of E-mail
from aspammer@website.com is spam.
Der ,,schnelle” braune Fuchs springt
&#64257;ber den faulen Hund. Le renard brun
«rapide» saute par-dessus le chien
paresseux. La volpe marrone rapida
salta sopra il cane pigro. El zorro
marrén répido salta sobre el perro
perezoso. A raposa marrom rzipida
salta sobre o c&#64257;o preguicoso.




```

---

### Post by 3togo on 2012-04-22
Many thanks

> **Irihapeti said:**
> ```
ja@ja-laptop:~$ python test.py
result(ProcessPagesBuffer)= The (quick) [brown] {fox} jumps!
Over the $43,456.78 <lazy> #90 dog
& duck/goose, as 12.5% of E-mail
from aspammer@website.com is spam.
Der ,,schnelle” braune Fuchs springt
&#64257;ber den faulen Hund. Le renard brun
«rapide» saute par-dessus le chien
paresseux. La volpe marrone rapida
salta sopra il cane pigro. El zorro
marrén répido salta sobre el perro
perezoso. A raposa marrom rzipida
salta sobre o c&#64257;o preguicoso.

```
Had to do the "apt-get -f install" thing, too, before it would install properly.

---

