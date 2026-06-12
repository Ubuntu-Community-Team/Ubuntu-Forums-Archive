---
title: "No more need to compile Wubi when creating  customs liveCD"
date: 2009-02-07
forum: Tutorials
---

### Post by ColleysForEver on 2009-02-07
Hi everybody,

If some one is interested, I've manage to make both remastersys and wubi working together.
I'm using a self modified version of wubi and remastersys.
First part is for Wubi.

Wubi is designed to use embedded files. The content of this embedded files is filled at compilation time. For my needs, I want a 'none power user' to be able to backup an existing system as a live CD with installation features and why not wubi features.
The main problem to do this was the need to setup and compile Wubi each time a new livecd is build. Now, you only need to do it one time.

The first step is to modify wubi to use external isolist.ini files.
[INDENT]To do this:
If not installed, download packages necessary to compile wubi
```

sudo apt-get update
sudo apt-get install build-essential unzip p7zip-full bzr-svn bzr gettext
```
and depending of your installation, maybe some other packages

Download the wubi sources.

More explaination are given in 
[http://ubuntuforums.org/showthread.php?t=682751&highlight=wubi+compile](http://ubuntuforums.org/showthread.php?t=682751&highlight=wubi+compile) if needed

```

mkdir wubi
cd wubi
bzr branch [http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy](http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy)
cd hardy

```
Compile wubi without modifications to check if everything is OK
```

sudo make prerequisites

```
note: when running this command, it stalled when trying to download libcurl sources. Maybe it because of a maintenance roll on the [http://curl.haxx.se](http://curl.haxx.se) site
if getting this problem, edit src/metadl/Makefile and change [http://curl.haxx.se/download/](http://curl.haxx.se/download/) with a mirror (eg [http://www.mirrorspace.org/curl/](http://www.mirrorspace.org/curl/))
```

make clean
make
make test

```
If every thing is allright, modify the wubi code to use an external isolist.ini
in wubi/src/variables.nsh
add 
```

var INIDIR
var plugin_ini

```
in wubi/src/main_page.nsh
in function
Function PopulateDistroList
 change
```
         ${GetSectionNames} "$PLUGINSDIR\data\isolist.ini" "AddDistroToList"

```
 for
```
         ${GetSectionNames} "$INIDIR\isolist.ini" "AddDistroToList"

```
in wubi/src/info.nsh

in function Function GetDistroInfo

change
```

    ReadINIStr $isoName $PLUGINSDIR\data\IsoList.ini "$distroFullName" "IsoName"
    ReadINIStr $isoSize $PLUGINSDIR\data\IsoList.ini "$distroFullName" "IsoSize"
    ReadINIStr $minIsoSize $PLUGINSDIR\data\IsoList.ini "$distroFullName" "MinIsoSize"
    ReadINIStr $isoKernel $PLUGINSDIR\data\IsoList.ini "$distroFullName" "kernel"
    ReadINIStr $isoInitrd $PLUGINSDIR\data\IsoList.ini "$distroFullName" "initrd"
    ReadINIStr $metalinkUrl $PLUGINSDIR\data\IsoList.ini "$distroFullName" "metalink"
    ReadINIStr $metalinkUrl2 $PLUGINSDIR\data\IsoList.ini "$distroFullName" "metalink2"
    ReadINIStr $distroPackages $PLUGINSDIR\data\IsoList.ini "$distroFullName" "packages"
    ReadINIStr $distroVersion $PLUGINSDIR\data\IsoList.ini "$distroFullName" "version"
    ReadINIStr $distroSubVersion $PLUGINSDIR\data\IsoList.ini "$distroFullName" "subversion"
    ReadINIStr $md5sums_filename $PLUGINSDIR\data\IsoList.ini "$distroFullName" "md5sums"
    ReadINIStr $md5sums_signature $PLUGINSDIR\data\IsoList.ini "$distroFullName" "md5sums_signature"
    ReadINIStr $cdFileCheck $PLUGINSDIR\data\IsoList.ini "$distroFullName" "cdFileCheck"
    ReadINIStr $cdmd5sums $PLUGINSDIR\data\IsoList.ini "$distroFullName" "cdmd5sums"    

```
by
```

    ReadINIStr $isoName $INIDIR\IsoList.ini "$distroFullName" "IsoName"
    ReadINIStr $isoSize $INIDIR\IsoList.ini "$distroFullName" "IsoSize"
    ReadINIStr $minIsoSize $INIDIR\IsoList.ini "$distroFullName" "MinIsoSize"
    ReadINIStr $isoKernel $INIDIR\IsoList.ini "$distroFullName" "kernel"
    ReadINIStr $isoInitrd $INIDIR\IsoList.ini "$distroFullName" "initrd"
    ReadINIStr $metalinkUrl $INIDIR\IsoList.ini "$distroFullName" "metalink"
    ReadINIStr $metalinkUrl2 $INIDIR\IsoList.ini "$distroFullName" "metalink2"
    ReadINIStr $distroPackages $INIDIR\IsoList.ini "$distroFullName" "packages"
    ReadINIStr $distroVersion $INIDIR\IsoList.ini "$distroFullName" "version"
    ReadINIStr $distroSubVersion $INIDIR\IsoList.ini "$distroFullName" "subversion"
    ReadINIStr $md5sums_filename $INIDIR\IsoList.ini "$distroFullName" "md5sums"
    ReadINIStr $md5sums_signature $INIDIR\IsoList.ini "$distroFullName" "md5sums_signature"
    ReadINIStr $cdFileCheck $INIDIR\IsoList.ini "$distroFullName" "cdFileCheck"
    ReadINIStr $cdmd5sums $INIDIR\IsoList.ini "$distroFullName" "cdmd5sums"
	

```	
	
in function Function parse_command_line_parameters
add
```

##begin of modified code
    strcpy $INIDIR $EXEDIR
    ##messagebox mb_ok "$INIDIR"
    ##messagebox mb_ok "$EXEDir"
    ${StrStr} $str $CMDLINE "--plugin_ini"
    ${if} "$str" != ""
        strcpy $plugin_ini true
        strcpy $INIDIR "$PLUGINSDIR\data"
	##messagebox mb_ok "$INIDIR"
    ${endif}
##end of modified code

```    
	
Compile the modified wubi
```

make clean
make 
make test

```
Now you have a wubi executable able to read an isolist.ini located in the same directory than the wubi executable itself. By this way, your don't need to compile a new wubi executable everytime you are creating a new live cd.
It is now very easy to create this isolist.ini to suite your own live cd. The easyest way to do it, is to make it being automaticaly created with remastersys.
The new wubi executable comes with a new command line option "--plugin_ini" to keep compatibility with build-in isolist.ini

What we need to use wubi with a live cd is
[INDENT]- wubi executable on the cd tree
- a correct isolist.ini in the same directory than the wubi executable[/INDENT]
This isolist.ini must be formated with distro name and version informations.[/INDENT]
Second part, modifing remastersys 
[INDENT]As said before the isolist.ini will be created during the liveCD creation process with Remastersys.
First step in remastersys is to create new parameters that will be used to create the isolist.ini file

To create a live / dist cd  remastersys use a CD label, and an iso file name.
[INDENT]- Cd label will be use as the the distro name.
- version don't exist so we need to add it[/INDENT]
in remastersys_gui
in fonction modifymenu ()
add
```

elif [ "$MODIFY" = "g" ]; then
ISOVER=`$DIALOG $TITLE"Remastersys Backup" $ENTRY $TEXT"Enter new revision" $ENTRYTEXT"$ISOVER"`
if [ "$ISOVER" = "" ]; then
ISOVER="0.0.1"
fi
elif [ "$MODIFY" = "h" ]; then
WUBIURL=`$DIALOG $TITLE"Remastersys Backup" $ENTRY $TEXT"Enter URL to use with wubi" $ENTRYTEXT"$WUBIURL"`
if [ "$WUBIURL" = "" ]; then
WUBIURL="http://something"
fi

```
and modify line
```

MODIFY=`$DIALOG $TITLE"Remastersys Backup" $MENU $TEXT"Please Select which option you would like to change?" a "Username = $LIVEUSER" b "Title = $LIVECDLABEL" c "Filename = $CUSTOMISO" d "Working Directory = $WORKDIR" e "Files to Exclude = $EXCLUDES" f "CD Boot Method = $CDBOOTTYPE" q "Go back to main menu"`

```
to 
```

MODIFY=`$DIALOG $TITLE"Remastersys Backup" $MENU $TEXT"Please Select which option you would like to change?" a "Username = $LIVEUSER" b "Title = $LIVECDLABEL" g "Version =$ISOVER" h "Url =$URL" c "Filename = $CUSTOMISO" d "Working Directory = $WORKDIR" e "Files to Exclude = $EXCLUDES" f "CD Boot Method = $CDBOOTTYPE" q "Go back to main menu"`

```
add also the new parameter in the remastersys config file template in the same file (below cat > /etc/remastersys.conf <<FOO)
```

# Here you can give a revision number
ISOVER="$ISOVER"

# Here you can give a URL to use with Wubi to download the iso
WUBIURL="$WUBIURL"

```
Now that this parameters are created , they must be filled to suite the X.Y.Z format needed by wubi

For convenience, the iso file name will be compose with the file name given plus the version plus ".iso":it no more needed to add the file extention  


In remastersys, add some code to create isolist.ini
first create /etc/remastersys/wubi directory and add an isolist.ini template in /etc/remastersys/wubi
```

[__DISTRO__-i386]
version=__VERSION__
subversion=
isoName=
packages=
kernel=casper\vmlinuz
initrd=casper\initrd.gz
metalink=__URL__/__DISTRO__-__VERSION__-i386.metalink
metalink2=
md5sums=MD5SUMS-metalink
md5sums_signature=MD5SUMS-metalink.gpg
isoSize=
minIsoSize=600000000
cdFileCheck=casper\filesystem.squashfs
cdmd5sums=md5sum.txt

[__DISTRO__-amd64]
version=__VERSION__
subversion=
isoName=
packages=
kernel=casper\vmlinuz
initrd=casper\initrd.gz
metalink=__URL__/__DISTRO__-__VERSION__-amd64.metalink
metalink2=
md5sums=
md5sums_signature=
isoSize=
minIsoSize=
cdFileCheck=casper\filesystem.squashfs
cdmd5sums=md5sum.txt

```
If you want, add also an autorun.inf in the same directory to get autostart cd features 
```

[autorun]
open=Wubi.exe
icon=Wubi.exe

```
And the most important, copy the wubi executable you get in first step to /etc/remastersys/wubi/wubi.exe

Now it is time to add some new stuff to remastersys
 after 
```

if [ "$LIVECDLABEL" = "" ]; then
LIVECDLABEL="Custom Live CD"
fi

```
add 
```

if [ "$ISOVER" = "" ]; then
ISOVER="0.0.1"
fi

if [ "$WUBIURL" = "" ]; then
WUBIURL="http://something/"
fi

```
Somewere in part "STEP3 of remastersys add 
```

## creation fichier ./disk/info
mkdir -p $WORKDIR/ISOTMP/.disk
echo "$LIVECDLABEL $ISOVER "'"HH"'" - Release i386 ($(date +%d%m%y))" > $WORKDIR/ISOTMP/.disk/info
## fin

## creation repository pour lupin-support et wubi
apt-get -d -y --reinstall install lupin-support
mkdir -p $WORKDIR/ISOTMP/pool
mkdir -p $WORKDIR/ISOTMP/pool/lupin
cp /var/cache/apt/archives/lupin-support*.deb $WORKDIR/ISOTMP/pool/lupin/
mkdir -p $WORKDIR/ISOTMP/dists
mkdir -p $WORKDIR/ISOTMP/dists/hardy
mkdir -p $WORKDIR/ISOTMP/dists/hardy/main
mkdir -p $WORKDIR/ISOTMP/dists/hardy/main/binary-i386
dpkg-scanpackages $WORKDIR/ISOTMP/pool/lupin /dev/null > $WORKDIR/ISOTMP/dists/hardy/main/binary-i386/Packages
sed -i s#$WORKDIR/ISOTMP/## $WORKDIR/ISOTMP/dists/hardy/main/binary-i386/Packages
cat $WORKDIR/ISOTMP/dists/hardy/main/binary-i386/Packages | gzip -9c > $WORKDIR/ISOTMP/dists/hardy/main/binary-i386/Packages.gz

cp /etc/remastersys/wubi/* $WORKDIR/ISOTMP/
sed -i 's#__VERSION__#'"$ISOVER"'#g' $WORKDIR/ISOTMP/isolist.ini
sed -i 's#__DISTRO__#'"$LIVECDLABEL"'#g' $WORKDIR/ISOTMP/isolist.ini
sed -i 's#__URL__#'"$WUBIURL"'#g' $WORKDIR/ISOTMP/isolist.ini

##fin

```
another modification (not related to wubi usage) is to be donne in part step 5 of remastersys to make persistent mode available with ubuntu 8.04
```
  
# Step 5 plus :correction du bug casper
rm -rf $WORKDIR/initrd-remake

mkdir $WORKDIR/initrd-remake
cd $WORKDIR/initrd-remake
mkdir initrd-old
cp $WORKDIR/ISOTMP/casper/initrd.gz initrd_old.gz
cd initrd-old
gunzip < ../initrd_old.gz | cpio -i --make-directories
cd scripts
#editer casper et enlever ,mode=755
#vi casper
sed -i s/,mode=755// casper

cd ..
find ./ | cpio -H newc -o > ../initrd
cd ..
gzip initrd
cp initrd.gz $WORKDIR/ISOTMP/casper/
cd ..

#fin du step5 plus

```

And finaly, modify step 8 of remastersys to add $ISOVER to the filename and label of the CD where necessary
$LIVECDLABEL -> $LIVECDLABEL-$ISOVER
$CUSTOMISO -> $CUSTOMISO-$ISOVER.iso
```

# Step 8 - Make the ISO file
# ajout "-$ISOVER au bout de $LIVECDLABEL
# Step 8 - Make the ISO file

echo "Creating $CUSTOMISO-$ISOVER.iso in $WORKDIR"
$CREATEISO    \
 -quiet \
 -r    \
 -V "$LIVECDLABEL-$ISOVER"    \
 -cache-inodes    \
 -J    \
 -l    \
 -b isolinux/isolinux.bin    \
 -c isolinux/boot.cat    \
 -no-emul-boot    \
 -boot-load-size 4    \
 -boot-info-table    \
 -o $WORKDIR/$CUSTOMISO-$ISOVER.iso "$WORKDIR/ISOTMP" 2>>$WORKDIR/remastersys.log 1>>$WORKDIR/remastersys.log

else

#grub mode

# remove files that change and cause problems with checking the disk
sed -e '/boot/d' md5sum.txt > md5sum.txt.new
sed -e '/md5sum/d' md5sum.txt.new > md5sum.txt
rm -f md5sum.txt.new

sleep 1

# ajout "-$ISOVER au bout de $LIVECDLABEL
# Step 8 - Make the ISO file
echo "Creating $CUSTOMISO-$ISOVER.iso in $WORKDIR"
$CREATEISO    \
 -quiet \
 -r    \
 -V "$LIVECDLABEL-$ISOVER"    \
 -cache-inodes    \
 -J    \
 -l    \
 -b boot/grub/stage2_eltorito    \
 -no-emul-boot    \
 -boot-load-size 4    \
 -boot-info-table    \
 -o $WORKDIR/$CUSTOMISO-$ISOVER.iso "$WORKDIR/ISOTMP" 2>>$WORKDIR/remastersys.log 1>>$WORKDIR/remastersys.log

fi

# create the md5 sum file so the user doesn't have to - this is good so the iso file can later be tested to ensure it hasn't become corrupted



echo "Creating $CUSTOMISO-$ISOVER.iso.md5 in $WORKDIR"


md5sum $WORKDIR/$CUSTOMISO-$ISOVER.iso > $WORKDIR/$CUSTOMISO-$ISOVER.iso.md5

sleep 1


echo "$WORKDIR/$CUSTOMISO-$ISOVER.iso is ready to be burned or tested in a virtual machine."
echo " "
echo "Check the size and if it is larger than 700MB you will need to burn it to a dvd"
echo " "
ls -hs $WORKDIR/$CUSTOMISO-$ISOVER.iso
echo " " 
echo "It is recommended to run 'sudo remastersys clean' once you have burned and tested the $CUSTOMISO"
echo " "

```
[/INDENT]

If every thing is ok , remastersys will be able to create some backups/live/dist CD that can be installed easyly in XP/VISTA PC's with wubi

In addition, some little thing may to be done to work properly:
[INDENT]- it seems that lupin-support / casper-lupin need to be installed on the system before creating the live cd with remastersys,
even if , like it done in the modified remastersys script, a mini repository with the package is embeded in the live CD
- depending the way boot menu of the livecd is set by remastersys, add options to start live cd in installation mode. Here is the config file I am using with my customized gfxboot bootmenu manager
```

DEFAULT live
GFXBOOT bootlogo
APPEND  file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL live
  menu label ^Live CD
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/custom.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL install
  menu label ^Installation 
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/custom.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
LABEL persistent
  menu label ^Live CD Persistent
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/custom.seed boot=casper persistent initrd=/casper/initrd.gz quiet splash --
LABEL vesapersistent
  menu label ^Live CD Persistent mode vesa
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/custom.seed boot=casper xforcevesa persistent initrd=/casper/initrd.gz quiet splash --
LABEL vesa
  menu label ^Live CD mode vesa
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/custom.seed boot=casper xforcevesa initrd=/casper/initrd.gz quiet splash --
LABEL check
  menu label ^Verification CD
  kernel /casper/vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
LABEL memtest
  menu label ^Test memoire
  kernel /isolinux/memtest
  append -
LABEL hd
  menu label ^Demarrage HD
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt


``` 
- If like me ( i'm using lxde) , you want to use other window manager than Metacity (gnome), Kde or flux box, you will need to modify the ubiquity script in order to start lxde properly before installing the system.
in /usr/bin/ubiquity-dm
after 
```

            elif osextras.find_on_path('xfwm4'):
                wm = subprocess.Popen('xfwm4',
                    stdin=null, stdout=logfile, stderr=logfile,
                    **maybe_drop_privileges)

```
add code to start openbox (replace by your own window manager if needed)
```

            elif osextras.find_on_path('openbox'):
                wm = subprocess.Popen('openbox',
                    stdin=null, stdout=logfile, stderr=logfile,
                    **maybe_drop_privileges)

```
[/INDENT]

This howto have been written after the job was done (and worked), maybe some small mistakes may be found in the codes given.
Any feedback will be welcome in order to correct this post.

One usage I have done was to install UbuntuStudio (Ubuntustudio distro CD don't support wubi) on XP computer with wubi.
[indent]
 -Virtual machine installation of UbuntuStudio
 -Wubi enabled live CD with Remastersys creation
 -Ubuntustudio installation on NTFS partition with wubi
[/indent]

---

### Post by grndslm on 2009-02-24
WOW... This is the last thing I've been trying to get working with remastersys.

This is just the kinda example instructions I need for my [ULTIMATE Remastersys Guide](http://ubuntuforums.org/showthread.php?t=1073838).  I'll have to read your post over whenever it's not Mardi Gras!!! .. and then I'll add this final piece to my treasure-full guide.

---

### Post by grndslm on 2009-02-25
OK... I've been bouncing around today, but I've had a few chances to glance at parts of this.  I'd like to start off by thanking you, because I never woulda been able to complete this by myself.

All I can correct for you is that your use of mkdir to create multiple directories is a little funny.

You can simply create all of the directories at once with the -p switch... so you can save a few lines by using these:

mkdir -p $WORKDIR/ISOTMP/pool/lupin/
mkdir -p $WORKDIR/ISOTMP/dists/hardy/main/binary-i386/
mkdir -p $WORKDIR/initrd-remake/initrd-old/

Also, I'm curious as to what the $WUBIURL variable is for... and if a separate $ISOVER variable is necessary for Wubi?  I really just scanned over your corrections, but I'm guessing it's not necessary as long as my $CUSTOMISO is labeled CustomDist-0.0.1, eh?  Perhaps there could be a correction to make sure the user enters in a version number in the x.y.z format?

And I'm wondering what Fragadelic is gonna think of this and if he'll just make some more corrections and eventually integrate it into his script.  He might over time, even tho he doesn't have a particular need for it right now.  I don't have a need for it either, but there's no sense in not putting Wubi on my dist since it's only 1.6 GB, and I've still got about 2.3 GB to go.

---

### Post by ColleysForEver on 2009-03-15
Thanks for your interest about my work,

First, I don't have the chance to work every day with linux, and I work mainly with the minimal number of instructions and options I know. So my mkdir are "funny" because I'm too lazy (or too busy)to take 30 seconds to read mkdir man pages .... 

$WubiUrl :Wubi is designed to be able install linux without cd, just by getting an iso file over the Internet. $WUBIURL is made to specify the URL to get this Iso file.


$ISOVER : Theres may be a way to use formated $Customiso variable to get a version number able to work with Wubi. I've simply use the quickest way that was to create a new variable (Lazy one more time ...).

---

### Post by arnoldus on 2009-06-06
I'm not sure if I understand, the windows .exe has to be rebuilt??

If I want to wubi install crunchbang linux from iso, can I just follow this guide to the letter? (or alternatively; installing ubuntu minimal)

---

### Post by ColleysForEver on 2009-06-07
Yes, the wubi.exe has to be rebuild:
Original wubi.exe contains compiled informations about the distro to install.
- You can compile a new wubi.exe with compiled isolist.ini information about your distro : see instructions on other threads to dot this.
- you can compile à new wubi.exe with extenal file isolist.ini support : follow my tutorial to modify the wubi sources.

If you dont' have a linux computer ready to compile wubi, your can do it several ways
- use mingw compiler in windows
- boot a linux live cd 
- install a linux distro into a virtual machine( qemu, vmware, virtualbox ...): this is the way I use  
 

What you also need is that your distro have lupin support (lupin-support, lupin-casper) and ubiquity support. If not , none version of wubi will be in order to install your distro. Depending of the windows manager your are using in your distro, your may also need to enable your Wm into ubiquity scripts.

If your are building your own distro
- add lupin and ubiquity : required
- add remastersys with modifications : not required but make build of the iso more easier and create the isolist.ini and ./disk/info files

If your want to install an existing distro and enable wubi installation with it, remaster your distro:
1)install your distro : severals ways :
- run live cd with persitence support
- use virtual machine to install your distro
- install natively your linux distro on hd
2)add lupin ubiquity support if needed
3)build your new iso : several ways :
-install remastersys with modifications
- install/use remastersys or any other remastering tools or method and take care manualy of isolist.ini, .disk/info and wubi.exe  

 As you see, you need both : a wubi executable, and a distro that have been made ready to be installed by wubi.

---

### Post by paok4 on 2009-06-12
Is it possible to provide me the modified remastersys to use it for making a custom cd with the the wubi installer in it ?  (I'm a new in all these and i cant do all this compiling !!! I really tried althought !!! ) Or i need something more than that ???

---

### Post by paok4 on 2009-06-13
i managed to compile wubi !!! But now how i create the ''isolist.ini and ./disk/info files'' to put in the ISO (next to modified WUBI isuppose) ???? An example maybe of an isolist.ini file ??? Help guys !!!

ps: I have already remastered the ISO i want to setup using WUBI by adding the lupin support (lupin-support, lupin-casper) and ubiquity support

---

### Post by paok4 on 2009-06-13
OK I did everything !!! 

Compiled Wubi OK
Modified Remastersys OK
Finally I created the live cd with custom isolist.ini and  wubi in it , burned it to a cd ...
Under windows vista the Wubi autoruns correctly and during the setup process is looking to connect to [http://something](http://something) !!! and the process stops after a few attempts ...
Why is not using the CD ??? Where is the problem ???

PS: the only thing that doesn't look correct to me is that the .DISK/info file in the generated ISO still says ''Ubuntu 8.10 "intrepid" - Release i386 (20090613)'' and not something like Custom CD bla bla bla ... Isn't that supossed to be generated differently from the modified remastersys ???

Any help ????

---

### Post by ColleysForEver on 2009-06-14
Did you take the remastersys I've send to you be email or the last revision of remastersys, As I have seen recently(correct it if I am wrong), the creation of .disk/info have been added into remastersys.
If it is , there may be conflict between the two parts of code.

---

### Post by paok4 on 2009-06-14
No i didn't get it !!! I've send you a pm with my email included , can you try again ???

---

### Post by mobile123 on 2009-07-06
well thanx for sharing dude.

---

### Post by paok4 on 2009-07-08
There is no problem sharing dude... There is serious problem with compiling of wubi sources (for the moment i hope). All the editions of wubi fail to be compiled because of missing resources downloading probably, during the process ... 

The mods for remastersys are working perfectly "only" in the 2.0.9 editition.So you have to apply them to this edition... In the latest edition 2.0.12 the custom.iso is not created at all ...


:popcorn::popcorn::popcorn:

---

### Post by paok4 on 2009-08-18
[LEFT]The "MONOMAXOS Greek Linux OS" where i'm member of the development team has released the latest ISO (ver. 4.0) based on Ubuntu 9.04 (it's a great ubuntu remix for amateur in Linux Greek speaking users) that has the characteristic of remastersys and wubi working together in the way [ColleysForEver]("http://ubuntuforums.org/member.php?u=721726") says at the start of the post without the need to compile wubi or changing the remastersys source code.

You can install it on your hard disk ,make your personal changes (add/remove packages), modify everything you like and simply create your new custom live cd by entering in the terminal 
```
" sudo remastersys backup custom.iso " 
```The new custom live CD/DVD will have embedded wubi support for installation inside windows !!! 

[CENTER][IMG]http://1.bp.blogspot.com/_UhCh8WrXlwY/SfRdbSI1OMI/AAAAAAAAABE/Le0hyHKPpYU/S240/256x256-blog.png[/IMG]


Take a look of the Monomaxos tux and a few screenshots ([image]("http://monomaxos.host56.com/images/0003.png")) !!!

From [HERE]("http://ftp.ntua.gr/pub/linux/monomaxos/monomaxos-4.0.en.iso") download the English version of MONOMAXOS live DVD. 

More information in English you can find[ HERE]("http://monomaxos.host56.com/eng.htm") . 

[Distrowatch]("http://distrowatch.com/table.php?distribution=monomaxos") page of Monomaxos
[/CENTER]
[/LEFT]

---

### Post by DediCATeD20 on 2011-06-12
Hi ColleysForEver,
Hi everybody,
 
does anybody have up to date instructions or tutorials, for remastering Ubuntu 10.4 Lucid Lynx with wubi?? 
 
Problem is that wubi for Lucid Lynx does not have variables.nsh, main_page.nsh and info.nsh.
 
 
Thanks very much,
DediCATeD

---

### Post by javanesse on 2011-07-09
that was great tutorials,but anybody can make tutorial by video mode please.

---

### Post by jibon_24 on 2011-11-15
hello everyone,

I am using ubuntu 11.10 & trying to do this process. But I got some error during Compile wubi. When I write this code```
sudo make prerequisites
``` I got this error:```
tools/build-prerequisites
make[1]: Entering directory `/home/shovon/wubi/hardy/src/metadl'
make[1]: `prerequisites' is up to date.
make[1]: Leaving directory `/home/shovon/wubi/hardy/src/metadl'
Checked out revision 59.
tools/build-prerequisites: 60: cannot open ../../wubi.patch: No such file
Checked out revision 23.

```

After writing this code ```
sudo make
``` I got this error:```
configure: error: GRUB requires a working absolute objcopy; upgrade your binutils
make: *** [wubildr] Error 1
```

But I am using the latest binutils ```
sudo apt-get install binutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
binutils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 102 not upgraded.
```

Any one can help me please>>>>>>>>>>>>>>>>

---

### Post by riddz on 2012-01-08
> **jibon_24 said:**
> hello everyone,

I am using ubuntu 11.10 & trying to do this process. But I got some error during Compile wubi. When I write this code```
sudo make prerequisites
``` I got this error:```
tools/build-prerequisites
make[1]: Entering directory `/home/shovon/wubi/hardy/src/metadl'
make[1]: `prerequisites' is up to date.
make[1]: Leaving directory `/home/shovon/wubi/hardy/src/metadl'
Checked out revision 59.
tools/build-prerequisites: 60: cannot open ../../wubi.patch: No such file
Checked out revision 23.

```

After writing this code ```
sudo make
``` I got this error:```
configure: error: GRUB requires a working absolute objcopy; upgrade your binutils
make: *** [wubildr] Error 1
```

But I am using the latest binutils ```
sudo apt-get install binutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
binutils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 102 not upgraded.
```

Any one can help me please>>>>>>>>>>>>>>>>


I am too having the same problem.. hope you update the tutorial so that wubi can be included in the ubuntu 11.10 distro....

---

