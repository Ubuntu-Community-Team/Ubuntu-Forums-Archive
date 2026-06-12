---
title: "HOWTO: Convert Roboform to KeePassX"
date: 2008-03-12
forum: Tutorials
---

### Post by odie5533 on 2008-03-12
I've read a few methods on how to convert from one to other, all of which required a surplus of programs and none of which came remotely close to the accuracy I wanted. Using PassCrypt, you can import _some_ passwords from Roboform and export them to csv. From there you have to hack your way to get it to work with KeePass and then import it into KeePassX. I've done it this way, but the problem is that PassCrypt is not very good at finding your passwords in the Roboform export file.

And thus, I present you with my simple python method. I migrated over 600 passwords with an estimated 95% accuracy.

This guide is for [KeePassX 0.30](http://www.keepassx.org/), but can also be used for regular [KeePass](http://keepass.info) (Follow the guide using KeePassX and save the database as a kdb file. Then just open the kdb in KeePass).

To install this version, in a terminal type ```
sudo dpkg --install keepassx_0.3.0a-0ubuntu1~ppa1_amd64.deb
```

1. On Windows, export your Roboform passwords to html. I used a 2-column layout but I do not believe this has any effect.

2. Copy and paste the following into a file called KeePassX.py in the same directory as your Roboform html backup:
```
import re

outputFilename = 'KeePass.xml'
inputFilename = 'Roboform.html'

def printHeader(out):
  out.write('<!DOCTYPE KEEPASSX_DATABASE>\r\n<database>\r\n<group>\r\n')

def printFooter(out):
  out.write('</group>\r\n</database>\r\n')

def makeOutput(out, desc, un, pw, url, comment):
  out.write('  <entry>\r\n')
  out.write('    <title>' + desc + '</title>\r\n')
  out.write('    <username>' + un + '</username>\r\n')
  out.write('    <password>' + pw + '</password>\r\n')
  out.write('    <url>' + url + '</url>\r\n')
  out.write('    <comment>' + comment + '</comment>\r\n')
  out.write('  </entry>\r\n')

def inVarz(val, varz):
  for var in varz:
    if re.search(val, var[0], re.I) and len(var) > 1 and var[1] != '*':
      return var[1]
  return ''    

def getVars(t):
  varz = []
  regTr = re.compile('<TR>(.*?)</TR>',re.S)
  regTd = re.compile('<TD>(.*?)</TD>',re.S)
  trs = regTr.findall(t)
  for tr in trs:
    tds = regTd.findall(tr)
    # Removes blank entires
    for td in tds:
      if td == '':
        tds.remove(td)
    varz.append(tds)
  return varz

def getUn(varz):
  un = ''
  un = inVarz('username', varz)
  if un == '':
    un = inVarz('uname', varz)
  if un == '':
    un = inVarz('user', varz)
  if un == '':
    un = inVarz('log', varz)
  if un == '':
    un = inVarz('mail', varz)
  if un == '':
    un = inVarz('name', varz)
  if un == '':
    un = inVarz('account', varz)
  if un == '':
    un = inVarz('member', varz)
  if un == '':
    un = inVarz('uid', varz)
  if un == '':
    un = inVarz('nick', varz)
  if un == '':
    un = inVarz('id', varz)
  return un

def getPw(varz):
  pw = ''
  pw = inVarz('pass', varz)
  if pw == '':
    pw = inVarz('pin', varz)
  if pw == '':
    pw = inVarz('key', varz)
  if pw == '':
    pw = inVarz('pw', varz)
  return pw

def getEmail(varz):
  mail = ''
  mail = inVarz('mail', varz)
  return mail

fin = open(inputFilename, "r")
f = fin.read()
fin.close()

# Mine was in UTF-16 (?!) so I decided to
# make a check incase yours was too
# It should handle UTF-8 by default
if ord(f[0]) == 255 and ord(f[1]) == 254:
  f = unicode(f, 'utf-16')
# I wonder what would happen if your file
# was ascii... Bah, no one would use ascii.

f = f.replace('<WBR>', '')
f = f.replace('<BR>','')
f = re.sub('<TR[^>]*?>','<TR>',f)
f = re.sub('<TD[^>]*?>','<TD>',f)

p = re.compile('<TBODY>.*?</TBODY>',re.S)
finds = p.findall(f)

out = open(outputFilename, 'w')
printHeader(out)
i = 0
for tbody in finds:
  varz = getVars(tbody)
  desc = varz[0][0]
  if len(desc)> 5 and desc.find('<TD>') != -1: #pmg hax...
    desc = desc[43:]
  url = varz[1][0]
  un = getUn(varz)
  pw = getPw(varz)
  email = getEmail(varz)
  makeOutput(out, desc, un, pw, url, email)
  i = i + 1

printFooter(out)
out.close()
print 'Converted ' + str(i) + ' passwords'
```

3. Edit the file and set the inputFilename to the html file you exported from Roboform.

4. In a terminal run ```
python KeePassX.py
```

5. Open KeePassX 0.30 and go to File > Import from > KeePassX XML

6. Locate the xml file created by the python script and load it into KeePassX.

Enjoy!

---

### Post by BoddhiC on 2008-04-25
Thank you, thank you, thank you :D

Worked like a charm. You have just solved one of my last true frustrations with Linux - absolutely awesome! Thank you for sharing your script \\:D/

---

### Post by Dragon ELEMENTAL on 2008-09-08
Thanx sooo much for this! - I really mean it, this has made transferring my 800+ logons from roboform really easy.


*** Sharing is Caring ***


Seriously, major thanx!

^_^

---

### Post by TheAbu on 2009-03-10
Thank you very much, worked like a charm and Roboform was really one of the few programs I actually missed from windows so it's great to have something to replace it :) Thank you, thank you, thank you :)

---

### Post by strongjz on 2009-04-06
Worked Great! Thank you.  I am now able to migrate fully from windows to Ubuntu.

---

### Post by avacomputers on 2009-07-16
I tried this and terminal says no file name.

python: can't open file 'KeePassX.py': [Errno 2] No such file or directory

---

### Post by avacomputers on 2009-07-16
> **avacomputers said:**
> I tried this and terminal says no file name.

python: can't open file 'KeePassX.py': [Errno 2] No such file or directory

NOw I get this. 

> SyntaxError: invalid syntax
>>> python KeePassX.py
  File "<stdin>", line 1
    python KeePassX.py
                  ^
SyntaxError: invalid syntax
>>> 


---

### Post by binbash on 2009-07-17
Tried it on my friend's PC, and works great.Thanks

---

### Post by avacomputers on 2009-07-17
> **binbash said:**
> Tried it on my friend's PC, and works great.Thanks

That's great, but I followed the instructions exactly and it did not work for me. Any help (other than saying it worked) would be awesome.

---

### Post by avacomputers on 2009-07-21
ANyone? I really need help with this.

---

### Post by Dragon ELEMENTAL on 2009-07-26
OMG dude - lolz.

*** read ALL of my post before you start to do this - you might actually decide you don't need to convert all of your passwords ***


1.  you have to go to the folder that has your Roboform html backup  (i recommend you make a folder in your home directory called 'roboform', and move your roboform html backup there).

2.  copy and paste the code into a new file called KeePassX.py **in the same folder** as your Roboform html backup  (in /home/yourusername/roboform/)

2.5 REMEMBER to edit the code to point to the html file you exported from roboform  (change line 4, i.e. "inputFilename = 'filename_of_exported_file.html'"

3.  open terminal and type this EXACTLY: (be VERY careful with letter case, abc in NOT the same as aBc!)

cd roboform/

(and then type or copy-paste this next line)

python ./KeePassX.py

4.  then you have to import from within keepass (read post #1 for the rest)

NOTE:  IF this still does not work - maybe there's a problem with your python installation?  


Okay, let me just quickly tell you that when I *permanently*  moved from Windows to LiNUX, I needed to convert all of my roboform to keepassx - HOWEVER, I'm now using LastPass, the firefox extension.  Basically, it's hella Wicked.
I *know* it's not open source yet which may be a problem for the security concious (but then neither is roboform).  However, I EXTENSIVELY researched the company before I decided to use it, and the lead developer, creator, and owner of LastPass was already a $50m+ millionaire BEFORE he started work on LastPass!  OMG!

Basically, it's REALLY popular, it's VERY actively developed, and has AMAZING features, a thousand times more than roboform, including full form saving, auto-filling passwords, etc!  Also, I, along with almost a million ppl so far, 40,000 in the past week! trust and use lastpass.  I truly trust it (like I said, the developer is already a super millionaire - just a true programmer at heart, so not a *possible* cheat like the developer of the Sxipper firefox extension).  

Anyway, you can have secure access to everything you choose to store in LastPass, from ANY firefox, it's all securely synced via their server, and it's just amazing - trust me, it's the ONLY way to go (unless you're EXTREMELY security concious, but like I said, roboform in closed source too).  
I've got everything in there, 4x credit cards (with auto-fill on my identity, adresses, etc), and 1700+ username & passwords!

Last point, I'm REALLY great at Mathematics, and now LiNUX!  I understand encryption like the back of my eyelids, & all of the technical explanations the developers of the LastPass extension have given so far are spot-on accurate, & the really great news is that the developers have said that they'd like to make it open source, & will do so down the line, but just want to give their project a really solid foundation first. 

See this:
[https://lastpass.com/help.php?topic=import&nw=1&fromwebsite=1](https://lastpass.com/help.php?topic=import&nw=1&fromwebsite=1)

Download here:
[https://addons.mozilla.org/en-US/firefox/addon/8542](https://addons.mozilla.org/en-US/firefox/addon/8542)

It's really worth it - I just can't imagine living without this extension - I'd literally go mad!


Whatever happens, REPLY BACK - I was watching a great movie when I got disturbed by your email (I forgot to unsubscribe, and I'm using Thunderbird & IMAP, so "in Soviet Russia" Email comes to me - ...I'm in the UK - just google-image search it).
Anyway - I can't believe I've taken so damn long writing all of this - its almost 1:20am - & I'm now forced between sleep and finishing an hour more of this great movie...).  Seriously though, REPLY BACK - you own me that much.


^_^

SiNGH

---

### Post by Alex131089 on 2009-11-22
Thank your for this script ! :)
I modified it (to handle some french terms & other), so here's my version : 
```

import re

outputFilename = 'KeePass.xml'
inputFilename = 'Roboform.html'

def printHeader(out):
  out.write('<!DOCTYPE KEEPASSX_DATABASE>\r\n<database>\r\n<group>\r\n')

def printFooter(out):
  out.write('</group>\r\n</database>\r\n')

def makeOutput(out, desc, un, pw, url, comment):
  out.write('  <entry>\r\n')
  out.write('    <title>' + desc + '</title>\r\n')
  out.write('    <username>' + un + '</username>\r\n')
  out.write('    <password>' + pw + '</password>\r\n')
  out.write('    <url>' + url + '</url>\r\n')
  out.write('    <comment>' + comment + '</comment>\r\n')
  out.write('  </entry>\r\n')

def inVarz(val, varz):
  for var in varz:
    if re.search(val, var[0], re.I) and len(var) > 1 and var[1] != '*':
      return var[1]
  return ''    

def getVars(t):
  varz = []
  regTr = re.compile('<TR>(.*?)</TR>',re.S)
  regTd = re.compile('<TD>(.*?)</TD>',re.S)
  trs = regTr.findall(t)
  for tr in trs:
    tds = regTd.findall(tr)
    # Removes blank entires
    for td in tds:
      if td == '':
        tds.remove(td)
    varz.append(tds)
  return varz

def getUn(varz):
  un = ''
  un = inVarz('username', varz)
  if un == '':
    un = inVarz('uname', varz)
  if un == '':
    un = inVarz('user', varz)
  if un == '':
    un = inVarz('log', varz)
  if un == '':
    un = inVarz('mail', varz)
  if un == '':
    un = inVarz('name', varz)
  if un == '':
    un = inVarz('account', varz)
  if un == '':
    un = inVarz('member', varz)
  if un == '':
    un = inVarz('uid', varz)
  if un == '':
    un = inVarz('nick', varz)
  if un == '':
    un = inVarz('id', varz)

  if un == '':
    un = inVarz('handle', varz)
  if un == '':
    un = inVarz('nic', varz)
  if un == '':
    un = inVarz('pseudo', varz)
  if un == '':
    un = inVarz('usr', varz)
  if un == '':
    un = inVarz('acc', varz)
  if un == '':
    un = inVarz('u', varz)
  if un == '':
    un = inVarz('alias', varz)
#session_key/session_password
#  if un == '' and len(varz) > 2 and len(varz[2]) > 1:
#    un = varz[2][1]
  return un

def getPw(varz):
  pw = ''
  pw = inVarz('pass', varz)
  if pw == '':
    pw = inVarz('pin', varz)
  if pw == '':
    pw = inVarz('key', varz)
  if pw == '':
    pw = inVarz('pw', varz)

  if pw == '':
    pw = inVarz('mdp', varz)
  if pw == '':
    pw = inVarz('code', varz)
#  if pw == '' and len(varz) > 3 and len(varz[3]) > 1:
#    pw = varz[3][1]
  return pw

def getEmail(varz):
  mail = ''
  mail = inVarz('mail', varz)
  return mail

fin = open(inputFilename, "r")
f = fin.read()
fin.close()

# Mine was in UTF-16 (?!) so I decided to
# make a check incase yours was too
# It should handle UTF-8 by default
if ord(f[0]) == 255 and ord(f[1]) == 254:
  f = unicode(f, 'utf-16')
# I wonder what would happen if your file
# was ascii... Bah, no one would use ascii.

f = f.replace('<WBR>', '')
f = f.replace('<BR>','')
f = re.sub('<TR[^>]*?>','<TR>',f)
f = re.sub('<TD[^>]*?>','<TD>',f)

p = re.compile('<TBODY>.*?</TBODY>',re.S)
finds = p.findall(f)

out = open(outputFilename, 'w')
printHeader(out)
i = 0
for tbody in finds:
  varz = getVars(tbody)
  desc = varz[0][0]
  if len(desc)> 5 and desc.find('<TD>') != -1: #pmg hax...
    desc = desc[43:]
  url = varz[1][0]
  un = getUn(varz)
  pw = getPw(varz)
  email = getEmail(varz)
  makeOutput(out, desc, un, pw, url, email)
  i = i + 1

printFooter(out)
out.close()
print 'Converted ' + str(i) + ' passwords'

```

Note that there is commented lines : 
```
#  if un == '' and len(varz) > 2 and len(varz[2]) > 1:
#    un = varz[2][1]
```
and
```
#  if pw == '' and len(varz) > 3 and len(varz[3]) > 1:
#    pw = varz[3][1]
```
You can comment them out to make a file that may contain informations not matched (it use the first and the second field if no user/pass is find), and use a diff tool (WinMerge for me) to recover unmatched information.

---

### Post by ellipsoid on 2011-01-23
For anyone who may be interested, I have a perl script that converts Roboform Passcards, Identities and Safenotes to a  KeePassX XML file that can be imported to KeePassX and KeePass v2.

It is available from Google Code at [http://code.google.com/p/robo2keepass/]("http://code.google.com/p/robo2keepass/")

The XML will maintain your Roboform group (folder) structure and has some configuration for icons and group names.

---

### Post by aklimatize on 2011-10-29
> **ellipsoid said:**
> For anyone who may be interested, I have a perl script that converts Roboform Passcards, Identities and Safenotes to a  KeePassX XML file that can be imported to KeePassX and KeePass v2.

It is available from Google Code at [http://code.google.com/p/robo2keepass/]("http://code.google.com/p/robo2keepass/")

The XML will maintain your Roboform group (folder) structure and has some configuration for icons and group names.

Hey, this worked great for me under Debian Squeeze, after changing the config options.  Thanks a lot!

---

