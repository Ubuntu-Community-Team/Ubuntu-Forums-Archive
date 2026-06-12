---
title: "HOWTO: post to usenet with Ubuntu"
date: 2008-02-09
forum: Tutorials
---

### Post by Martje_001 on 2008-02-09
Hi,
Because it's a bit hard to post (binary files) to Usenet with Linux, I decided to make this tutorial.

*Note: All commands, which you have to run in a terminal, are in code tags.*

**1.** First install a few programs
```
sudo apt-get install par2 newspost rar
```

**2.** Place the files you want to upload in a folder.

**3.** Most files on Usenet are in rar-files. You can create these rar-files with this command:
```
rar a "name of rar file" -v10m -m0 "/home/example/upload/"* 
```
Let me explain the command:
***name of rar file:*** This is the name of the rar-file. ".rar" will automatic be added.
***-v10m:*** Split the file(s) to a new rar-archive after 10 MB
***-m0:*** Set compression level (0-store...3-default...5-best).
***"/home/example/upload/"*:*** This means; rar everything in the folder '/home/example/upload'

**4.** Now we can create par files.
```
par2create -r10 -n7 "name of par file" /home/example/upload/*.rar*
```
***-r10:*** Percent par-files you want to create
***-n7:*** Number of par-files you want to create
***"name of par file":*** I don't want to explain this ;)
***/home/example/upload/*.rar****: means; Create par-files of everything in the folder */home/eample/upload*, which ends with .rar

**5.** Upload your files
```
newspost -i upload.eweka.nl -u USERNAME -p PASSWORD -f [email]noadress@gmail.com[/email] -n alt.binaries.boneless -y -s "SUBJECT" "/home/example/upload/*.part*" "/home/example/upload/*.par*"
```


*[SIZE="3"]Extra notes:[/SIZE]*
This is it. You can run commands after each one is done (with &&). Then it will be something like:
```
rar a "name of rar file" -v10m -m0 "/home/example/upload/"* && par2create -r10 -n7 "name of par file" /home/example/upload/*.rar* && newspost -i upload.eweka.nl -u USERNAME -p PASSWORD -f [email]noadress@gmail.com[/email] -n alt.binaries.boneless -y -s "SUBJECT" "/home/example/upload/*.part*" "/home/example/upload/*.par*"
```

---

### Post by marxian on 2008-05-06
I would very much like to use this, but newspost is not in the repositories of Hardy. Can I still use this program?

---

### Post by Martje_001 on 2008-05-06
Of course :)

i386:
```
wget http://nl.archive.ubuntu.com/ubuntu/pool/universe/n/newspost/newspost_2.1.1-4_i386.deb
sudo dpkg -i newspost_2.1.1-4_i386.deb
```

amd64:
```
wget http://nl.archive.ubuntu.com/ubuntu/pool/universe/n/newspost/newspost_2.1.1-4_amd64.deb
sudo dpkg -i newspost_2.1.1-4_amd64.deb
```

---

### Post by rabside on 2008-05-23
greate guide!
Only a question: why do you split file in rar of 10MB? isn't usefull bigger blocks? maybe 40MB?

---

### Post by Martje_001 on 2008-05-23
Thank you! And, yes, it is, but this is only an example.

---

### Post by rabside on 2008-05-25
Hi guys, 
this is a little script to automate the upload:

```

#!/bin/bash

#---------- config start----------
username="username"
password="password"
server="newsserver"
temppath="path of temp dir used to post material es: /media/dati/"
newsgroup="newsgroup, es: alt.binaries.multimedia.divx.italian"
poster="poster name, es: poster"
email="email address, es: poster@gmail.com" 
#---------- config end----------


error="false"
filename="$(basename $1)"
subject="${filename%.*}"



function checkLastCommand {
	if [ "$1" != "0" ]; then
		error="true"
	fi
}

#rar split of file
rar a "$temppath$filename" -v40m -m0 $1

#checkresult
checkLastCommand "$?"

#create par
if [ "$error" != "true" ]; then
	par2create -r10 -n7 "$temppath$filename" "$temppath"*.rar*
fi

#checkresult
checkLastCommand "$?"

#post
if [ "$error" != "true" ]; then
	newspost -i "$server" -u "$username" -p "$password" -f "$email" -n "$newsgroup" -y -s "$subject" "$temppath"*
fi

#checkresult
checkLastCommand "$?"

#delete tmpfile
if [ "$error" != "true" ]; then
	rm "$temppath"*
fi

```

I hope this help ;)

---

### Post by Martje_001 on 2008-05-25
I'm working on this myself, see this:
[http://www.xs4all.nl/~mgj1/bnewspost.htm](http://www.xs4all.nl/~mgj1/bnewspost.htm)

---

### Post by hq197 on 2008-08-29
Martje!! Thank you for you guide. It's very helpful. Rabside, how do i use your script? I get a > Cannot create path of temp dir used to post material es: /media/dati/.rar
No such file or directorybasename: missing operand
Try `basename --help' for more information. in konsole when i run the script. Basename --help didn't help me at all. I have no idea how to adjust the script (if it indeed needs that).

---

### Post by hq197 on 2008-08-29
Thanks for the script but can you help me out of my error message [http://ubuntuforums.org/showpost.php?p=5686659&postcount=8]("http://ubuntuforums.org/showpost.php?p=5686659&postcount=8")

---

### Post by rabside on 2008-08-29
You have to change the value of variable temppath. Choose what you want.

---

### Post by Crafty Kisses on 2008-08-29
Nice tutorial, very nicely typed and very smooth. :)

---

### Post by shabi123 on 2008-08-29
Give you the best recommendation
Serving over 225,000 customers,  AAA PharmacyOnline is your trusted source for the lowest possible prices for all of your prescription needs. At AAA PharmacyOnline your health is our number one concern. Our trained team of doctors and pharmacists make sure your purchasing experience is stress free and enjoyable.  We make sure that you receive the highest quality medications. When it comes to excellent customer service, low prices and fast shipping, we set the industry standards. 
 
We offer a wide range of brand name and generic drugs at economical prices for all your prescription needs. If you find your medication priced lower, we will match that price for you.  
 
If you do not already have a prescription then our medical doctors can work with you to provide you with your prescription. 
 
Visit us: [http://www.aaa-pharmacyonline.com](http://www.aaa-pharmacyonline.com)

---

### Post by Stan* on 2008-10-06
I can't upload all the rar-files in a directory. When I type "~/Desktop/up/*.rar" I get an error: "WARNING: No such file or directory". What can I do to solve this?

Thanks.

---

### Post by hq197 on 2008-10-08
> **Stan* said:**
> I can't upload all the rar-files in a directory. When I type "~/Desktop/up/*.rar" I get an error: "WARNING: No such file or directory". What can I do to solve this?

Thanks.

Hi Stan,
Have u checked what directory your terminal is working from? To the left of your cursor and inside square brackets eg. [userisme@localhost Download] in this case, i am inside /home/userisme/Download/. If i passed a location like rar a example /Download/*.avi , i would get the same error message u did (unless there is a location like /home/userisme/Download/Download .

 In the end, the best is to operate from inside the actual data directory, so your command starts with the command, rather than a location.

---

### Post by Stan* on 2008-10-08
Thanks for your reply. I found it out already, I had to remove the quotes. Thanks anyway :)

---

### Post by DCJuggler on 2008-11-14
Hi,

Thanks for this, but there is just one problem, is there anyway to open more than 1 thread (aka upload more than 1 file at a time) as i cant max my server out with just a single thread which means it takes it longer to upload...

---

### Post by colemar on 2009-09-21
I bet you can figure out how to install: ksh, rar, par2, newspost.

```
#!/usr/bin/ksh

# tousenet

#---------- begin config ----------
SERVER=my.news.server.com
PORT=119
USERNAME=colemar
PASSWORD=password
NEWSGROUP=alt.binaries.test
EMAIL=colemarc@gmail.moc
NICKNAME=colemar
WORKBASE=/tmp/tousenet
RARVOLSIZE=50m
PARPERCENT=5
NFOMASK=*.nfo
SAMPLEMASK=*.sample.*
LISTFILESUFFIX=list.nfo
#---------- end config ----------

function errorexit {
  print -u2 "ERROR: $1"
  exit 1
}

function usage {
  print "
  tousenet <what> [<where>] [<subject>]

  <what>    a directory containing the binary files you want posted to usenet.
  <where>   an optional comma separated list of newsgroup names (maximum 5).
            Default is alt.binaries.test.
  <subject> an optional string to be used to build the articles subject.
            Default is directory name of <what>.

  Files contained in <what> (and subdirs) are assembled in a set of rar/par
  files located in a work dir under the configured temp directory.
  The common <prefix> for rar/par filenames is the directory name of <what>.

  This program attempts to recognize whether a given <what> has already been
  assembled for posting. To detect this situation, the work dir is named after
  a fingerprint made from the first 8 characters of the md5 digest of <what>
  contents and a helper listfile is created in the work directory.
  "[fingerprint]" is also inserted at the beginning of articles subject; it
  can be used later to search and track the post via binsearch.info or
  other services.

  If *.nfo and/or *.sample.* files exist in <what> directory, they will be
  posted as such (besides in rar archive).
  To let binsearch.info report these files together with rar/par files, you
  should name them with the common prefix: <prefix>.nfo <prefix>.sample.mkv
  The first *.nfo file is automatically renamed to <prefix>.nfo in the
  work dir and posted as file number 0.

  Example: tousenet ~/media/W.La.Foca alt.binaries.movies.divx 'W la foca! (1982) IMDB:tt0084880 avi divx 720x576 italiano-mp3'
"
  exit
}

WHAT=$1
[[ $WHAT = "" ]] && usage
WHERE=${2:-$NEWSGROUP}

[[ $WHAT = /* ]] || WHAT=$PWD/$WHAT
[[ -d $WHAT ]] || errorexit "$WHAT should be a directory"
[[ -r $WHAT ]] || errorexit "$WHAT is not readable"
print "Source is $WHAT"

PREFIX=$(basename $WHAT)
[[ $PREFIX = *\ * ]] && errorexit "I don't like blanks in common prefix [$PREFIX]"
LISTFILE=$PREFIX.$LISTFILESUFFIX

SUBJECT="${3:-$PREFIX}"

cd $WHAT
what=$(find . -type f -printf '%P %s %T+\n')
typeset -L8 FINGERPRINT
print -- "$what" | md5sum | read FINGERPRINT junk
print "Fingerprint is $FINGERPRINT"

WORKDIR=$WORKBASE/$FINGERPRINT
print "Work dir is $WORKDIR"
mkdir -p $WORKDIR
cd $WORKDIR

if [[ $(print *) = "*" ]]; then
  rar a $PREFIX -r -v$RARVOLSIZE -m0 $WHAT || errorexit "RAR archiver failed"
  eval cp $WHAT/$NFOMASK $WHAT/$SAMPLEMASK .
  par2 c -r$PARPERCENT $PREFIX * || errorexit "PAR file creation failed"
  print -- "$what" > $LISTFILE
else
  print "Work dir is not empty"
  if [[ -f $LISTFILE ]]; then
    print "Post already assembled in the work dir"
    read answer?"Do you want to repost it? [Y/n] "
    [[ $answer = @(n|N) ]] && errorexit "Aborted"
  else
    errorexit "The work dir contains something unexpected"
  fi
fi

NFO=""
ls *.nfo | fgrep -v $LISTFILE | read infofile
if [[ $infofile > "" ]]; then
  [[ -f $PREFIX.nfo ]] || mv $infofile $PREFIX.nfo
  NFO="-e $PREFIX.nfo"
fi

newspost -T 3 -y -i $SERVER -z $PORT -u $USERNAME -p $PASSWORD -f $EMAIL -F $NICKNAME -n $WHERE -s "[$FINGERPRINT] $SUBJECT" $NFO *

print "Done. The assembled post is still in work dir $WORKDIR"
```

---

### Post by Hated On Mostly on 2010-01-13
> **DCJuggler said:**
> Hi,

Thanks for this, but there is just one problem, is there anyway to open more than 1 thread (aka upload more than 1 file at a time) as i cant max my server out with just a single thread which means it takes it longer to upload...


Finally a solution for people who use Linux.

[http://jbinup.com/en/](http://jbinup.com/en/)

---

### Post by hikaricore on 2010-02-04
> **Hated On Mostly said:**
> Finally a solution for people who use Linux.

[http://jbinup.com/en/](http://jbinup.com/en/)

Thanks for the link.  Exactly what I as lookin for. :)

---

### Post by AintJoe on 2010-07-11
I can't seem to find any ubuntu/debian package for newspost

---

### Post by colemar on 2010-07-24
> **AintJoe said:**
> I can't seem to find any ubuntu/debian package for newspost

I had to compile it from the source tarball found at:
[http://newspost.unixcab.org](http://newspost.unixcab.org)

I'm afraid there is probably no ready made package around.

---

### Post by rascalli on 2010-08-13
This looks good.

Is there also a sort of webui for this ?

So that you click on a folder & then select : Upload
And then you can select all options ?


Or otherwise another script you can place on a server, so people can upload without SSH Access

tx

---

### Post by sanderj on 2010-08-23
There's no newspost package for Lucid. Here's how to compile yourself from source:

So get the source from [http://newspost.unixcab.org/index.html#Download](http://newspost.unixcab.org/index.html#Download), and unpack it. 
Go into the unpack directory
Try to make it (you will get an error):

```

sander@quirinius:/tmp/newspost-2.1.1$ make
make main CFLAGS="-O2 -Wall" LIBS=""
make[1]: Entering directory `/tmp/newspost-2.1.1'
cd base ; make CC="gcc" CFLAGS="-O2 -Wall"
make[2]: Entering directory `/tmp/newspost-2.1.1/base'
gcc -O2 -Wall -o test test.c
In file included from newspost.h:40,
                 from test.c:20:
utils.h:29: error: conflicting types for ‘getline’
/usr/include/stdio.h:651: note: previous declaration of ‘getline’ was here
make[2]: *** [test] Error 1
make[2]: Leaving directory `/tmp/newspost-2.1.1/base'
make[1]: *** [main] Error 2
make[1]: Leaving directory `/tmp/newspost-2.1.1'
make: *** [opt] Error 2
sander@quirinius:/tmp/newspost-2.1.1$ 

```

The solution is easy:

```
find . -type f -exec grep -l "getline" {} \; | xargs sed -i "s/\<getline\>/getline_/g"
```

Then make again, which will go OK.

---

### Post by AintJoe on 2010-08-25
If anyone is interested, I posted the code here, [http://github.com/joehillen/newspost](http://github.com/joehillen/newspost)

I'll create a debian package and GUI as soon as I feel like it. ;)

---

### Post by sanderj on 2010-08-25
> **AintJoe said:**
> If anyone is interested, I posted the code here, [http://github.com/joehillen/newspost](http://github.com/joehillen/newspost)

I'll create a debian package and GUI as soon as I feel like it. ;)

... and include in the the package the script that takes care of the rar, par and posting? ;-)

---

### Post by AintJoe on 2010-08-25
...or at least add it to the gui.

---

### Post by sanderj on 2010-09-11
The script seems to work for me, but my test posts do not appear in the newsgroup alt.binaries.test nor binsearch.info.


EDIT: the post did appear after 10 minutes on the newsserver, and after 20 minutes on binsearch.info.

SO: all OK!



```
...
Posted 10 files (13.5 MB encoded) in 2 minutes 21 seconds.     98 KB/second 
Done. The assembled post is still in work dir /tmp/tousenet/f64bee3c
```

---

### Post by parapapapapa on 2010-10-21
I have a question about making par2 files, like number 4 in the opening post.
> **Martje_001 said:**
> Hi,


**4.** Now we can create par files.
```
par2create -r10 -n7 "name of par file" /home/example/upload/*.rar*
```***-r10:*** Percent par-files you want to create
***-n7:*** Number of par-files you want to create
***"name of par file":*** I don't want to explain this :wink:
***/home/example/upload/*.rar****: means; Create par-files of everything in the folder */home/eample/upload*, which ends with .rar



I did this, and got:
```
~$ par2create -r10 filename.par2 filename.part*.rar
You must specify a list of files when creating.
```Then I did this and got:
```
~$ par2create -r10 filename*.par2 filename.part*.rar
You must specify a Recovery file.
```What am I doing wrong? I'm a beginner but I don't want to use the graphical version, I want to learn this.

---

### Post by brashley46 on 2011-01-15
> **hikaricore said:**
> Thanks for the link.  Exactly what I as lookin for. :)

;) YES. Tested nd it works. THANK YOU!

---

### Post by sanderj on 2011-01-18
> **rabside said:**
> Hi guys, 
this is a little script to automate the upload:

<snip>

I hope this help ;)

Great, very helpful script. Some remarks:

- I believe the script puts the full path in the upload which cause the full path (like /home/sander/...) to be in the download. I've changed that myself by cd-ing to the working directory and changing the newspost parameter at the end
- I've modified the script to include the PID ($$) in the working directory and in the subject, so that you can recognize the post and run multiple instances at the same time.
- the script can't handle spaces in a directory (and maybe file) name. See below. That's strange, because 'basename' itself can handle it. I don't know the solution; I'm not a bash guru (maybe just some extra quotes or parentheses?)


```

sander@athlon64:~/newspost2$ ./postenmaar.sh /home/sander/spaties\ in\ deze\ directory\ naam/
basename: extra operand `deze'
Try `basename --help' for more information.

RAR 3.90 beta 2   Copyright (c) 1993-2009 Alexander Roshal   3 Jun 2009
Shareware version         Type RAR -? for help

Evaluation copy. Please register.

Cannot open /home/sander/spaties
No such file or directory
Cannot open in
No such file or directory
Cannot open deze
No such file or directory
Cannot open directory
No such file or directory
Creating archive /home/sander/postenmaar-temp/.rar

WARNING: No files
sander@athlon64:~/newspost2$

```


[/CODE]

---

### Post by HackedServer on 2011-02-24
Unfortunately newspost doesn't have NZB support.

After asked around I found out about newsmangler. It supports multiple connections and nzb creation. 

[https://github.com/madcowfred/newsmangler](https://github.com/madcowfred/newsmangler)

---

### Post by sanderj on 2011-02-25
> **HackedServer said:**
> Unfortunately newspost doesn't have NZB support.

After asked around I found out about newsmangler. It supports multiple connections and nzb creation. 

[https://github.com/madcowfred/newsmangler](https://github.com/madcowfred/newsmangler)

Nice. Does this script generate par2 file? I see par2 is a commandline option, but the TODO says:

docs/TODO:* Add PAR2 generation. Read the par2cmdline source to work out how it decides


... so I wonder about par2 ...

---

### Post by Sharpie1 on 2011-07-10
I've been trying to post some test files with newspost but get the following error...
```
me@my-laptop:~/ys$ newspost -i news.mysip.com -u [EMAIL="me@myisp.co.uk"]me@myisp.co.uk[/EMAIL] -f [EMAIL="noadress@gmail.com"]noadress@gmail.com[/EMAIL] -n alt.binaries.test.files -y -s TYS_Test /home/me/ys/*.part* /home/me/ys/*.par*

WARNING: duplicate filename /home/me/ys/TYSSubsplus45avi.part1.rar - IGNORING
WARNING: duplicate filename /home/me/ys/TYSSubsplus45avi.part2.rar - IGNORING
WARNING: duplicate filename /home/me/ys/TYSSubsplus45avi.part3.rar - IGNORING
WARNING: duplicate filename /home/me/ys/TYSSubsplus45avi.part4.rar - IGNORING
WARNING: duplicate filename /home/me/ys/TYSSubsplus45avi.part5.rar - IGNORING
Calculating CRCs... done

From: [EMAIL="noadress@gmail.com"]noadress@gmail.com[/EMAIL]
Newsgroups: alt.binaries.test.files
Subject: TYS_Test

10 Files: 89.3 MB
Yencoding 89.3 MB total and posting to news.myisp.com

Posting in 1 second...             Segmentation fault
```Not much to go on I know, sorry...
I installed the recent deb with
```
sudo dpkg -i newspost_2.1.1-4_i386.deb
```any ideas ?

cheers
Sharpie1

(I have edited personal info out of the code !)

---

### Post by Sharpie1 on 2011-07-14
I finally got it running:
following Martje_001's original post I installed newspost, 
made a folder with the file to be posted in it
 using that folder as my working directory, I issued the following commands in terminal:
```
rar a <filename with filetype omitted> -v25m -m0
```this makes 25MB rar files (with the correct usenet naming convention) of everything in the folder (remove the handles < and >)
then :
In the working directory: 
```
par2create -r10 -n7 <filename with filetype omitted> *.rar*
```this creates 7 10% par files of the rars in the folder

I then removed the original file from the folder, leaving the nfo file, the rars and the pars

Then, using that folder as my working directory, I issued the following commands:
```
newspost -d -i news.myisp.com -f myname@myisp.com -F 'My Nickname'
``` (include the single quotes around the Nickname)
This sets the default newsserver, email address and Name for newspost
Then issued the posting command
```
newspost -n alt.my.group.name -y -s Subject_Line_of_My_Posting *
```
***this yencodes and posts everything in the working folder so make sure your working directory is correct before posting the contents of your home folder !!!!****

cheers
Sharpie1

---

### Post by Ultra Cronic on 2012-07-31
> **Martje_001 said:**
> Hi,
Because it's a bit hard to post (binary files) to Usenet with Linux, I decided to make this tutorial.

*Note: All commands, which you have to run in a terminal, are in code tags.*

**1.** First install a few programs
```
sudo apt-get install par2 newspost rar
```**2.** Place the files you want to upload in a folder.

**3.** Most files on Usenet are in rar-files. You can create these rar-files with this command:
```
rar a "name of rar file" -v10m -m0 "/home/example/upload/"* 
```Let me explain the command:
***name of rar file:*** This is the name of the rar-file. ".rar" will automatic be added.
***-v10m:*** Split the file(s) to a new rar-archive after 10 MB
***-m0:*** Set compression level (0-store...3-default...5-best).
***"/home/example/upload/"*:*** This means; rar everything in the folder '/home/example/upload'

**4.** Now we can create par files.
```
par2create -r10 -n7 "name of par file" /home/example/upload/*.rar*
```***-r10:*** Percent par-files you want to create
***-n7:*** Number of par-files you want to create
***"name of par file":*** I don't want to explain this ;)
***/home/example/upload/*.rar****: means; Create par-files of everything in the folder */home/eample/upload*, which ends with .rar

**5.** Upload your files
```
newspost -i upload.eweka.nl -u USERNAME -p PASSWORD -f [EMAIL="noadress@gmail.com"]noadress@gmail.com[/EMAIL] -n alt.binaries.boneless -y -s "SUBJECT" "/home/example/upload/*.part*" "/home/example/upload/*.par*"
```
*[SIZE=3]Extra notes:[/SIZE]*
This is it. You can run commands after each one is done (with &&). Then it will be something like:
```
rar a "name of rar file" -v10m -m0 "/home/example/upload/"* && par2create -r10 -n7 "name of par file" /home/example/upload/*.rar* && newspost -i upload.eweka.nl -u USERNAME -p PASSWORD -f [EMAIL="noadress@gmail.com"]noadress@gmail.com[/EMAIL] -n alt.binaries.boneless -y -s "SUBJECT" "/home/example/upload/*.part*" "/home/example/upload/*.par*"
```

Good God!! they need a GUI for this. I have waisted 4 nights sluthing the forums and google and DuckDuckGo searches and seams as though Linux is a total failure with usenet posting/reading file split Yenc management . As much as I HATE windows I miss NewsBin pro, it's hard to believe their is no Ubuntu counterpart not even close, Pan=fail/ knode=FAIL/ major missing features. especially uploading to the usenet. Files need to be split and yEnc coded automatically and nzb's created with nfo files all integrated in the upload process. 
I can't believe the fantastic intelligent support for Linux now and they are so out of the loop with the Usenet. and Oh Ya support for SSL port 563 connections a must now with newsreader/writer/posters. Most of us [especially mine] have all these programs in our systems as Xterminal command line programs and craplications, The GUI developement is a disgrace for these.:(
I hate the fact that I have 1 windows box [laptop] on hand for when I want to sleuth the newsgroups. Linux can't touch Newbin pro. Reads writes manages corupt files [PAR] a nd auto eYenc upload and download, preview  even tells me if the files are Password protected apon commanding a download as not to waist my time.
Auto handles nzb's  [Usenet shortcut to files]. and creates them too. I'd pay a hundred dollars for a Linux version of NewsBin pro right now. NO it doesn't fly in Wine, as is most of the case.](*,):rolleyes:

---

### Post by Ultra Cronic on 2012-07-31
Seems as though the linux community really needs a website possible commercial that does all of the intricate manipulations to a binary file attachment needed in order to post to usenet.
It would have to have a "Profile data base " so you enter your usenet account info over an ssl port maybe even need an IPsec key to secure it and then have a powerful web GUI to handle uploads. Of course people that are on the edge of society or in my case paranoia of privacy data mining [spying is immoral etc..] would not like it, but heck, I don't see Linux's developers as having any intention of fixing this Layman's way [GUI] to post to usenet problem. There used to be a Newsgroup service out there that had a web interface but I forget who it was.:popcorn::guitar:

---

### Post by Ultra Cronic on 2012-07-31
> **Hated On Mostly said:**
> Finally a solution for people who use Linux.

[http://jbinup.com/en/](http://jbinup.com/en/)

JbinUP has some qwerky demands on JAVA 2.6 from SUN.
Witch in my case may send Openshot video editor and other proggys to the sharts.
This is what happens when one depends on "other" peoples work to make "Their" program work. [As in I-PAD's JAVA crippling]  Just a little system upgrade so often causes UN-intended consequences that turn programs into  pile of binary bile. A more "Self Contained" attitude has been longing for GUI driven nntp file uploads in linux. Such as  Putty, you can run it from a thumb-drive on another box without messing with the other box's OS to get it to work. I use it to create sslh multiplex tunnels to encrypt my internet activity entirely when using a VPN service that supports socks5 tunneling.
Not cheap but worth it. I cringe every time someone writes code that demands SUN JAVA in order for it to work, I wish linux would stick with the GNU/SDK versions of it when they need JAVA.
Sincerely; The Ultra Cronic disgruntled network technician working on his second stroke and third heart attack.
:popcorn::guitar:

---

### Post by Antonio19 on 2013-04-13
For those interested I found the package newspost_2.1.1-4_amd64.deb on the website debian-archive at this location :

[http://archive.debian.net/etch/amd64/newspost/download](http://archive.debian.net/etch/amd64/newspost/download)
[http://ftp.nl.debian.org/debian-archive/debian/pool/main/n/newspost/newspost_2.1.1-4_amd64.deb](http://ftp.nl.debian.org/debian-archive/debian/pool/main/n/newspost/newspost_2.1.1-4_amd64.deb)

It is working perfectly on Ubuntu Precise 12.04 amd64 ... Thanks all for the tutorials and all the good stuff.

---

