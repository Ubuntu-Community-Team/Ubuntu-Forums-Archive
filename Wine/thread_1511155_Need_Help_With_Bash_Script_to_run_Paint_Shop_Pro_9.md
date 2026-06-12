---
title: "Need Help With Bash Script to run Paint Shop Pro 9"
date: 2010-06-16
forum: Wine
---

### Post by edmondt on 2010-06-16
Been trying to figure this out for the past 4 hours...Grrr....

I know the Paint Shop Pro 9 is old, but in my opinion it is still better than GIMP for enhancing photos. 

The program runs fine, I just need help creating a temp dir based on pid, 

First The command I used to run it:
```
sh -c 'env WINEDEBUG="+file" WINEPREFIX="/home/edmondt/.wine" \
wine C:\\windows\\command\\start.exe /Unix /home/edmondt/.wine/dosdevices/c:/users/edmondt/Start\ Menu/Programs/Jasc\ Software/Jasc\ Paint\ Shop\ Pro\ 9.lnk 2>&1 | \
awk -f ~/Documents/My\ PSP\ Files/mkdir.mawk'
```

The mkdir.mawk contains the following (I'm debugging, so lots of print outs):
```
##Begin mkdir.mawk contents
$0 ~ /JSC/ {
  if ($0 ~ /not found in/ && $0 ~ /wine_nt_to_unix_file_name/) {
    temp=substr($0,2+index($0,"L\""));
print "temp:", temp;
    temp_len=index(temp, ".tmp")+3;
print "temp_len:", temp_len;
    temp=substr(temp,1,temp_len);
print "temp:", temp;
    temp_parts_qty=split(temp,temp_parts,"\\");
print "temp_parts_qty:",temp_parts_qty;

    dirname=substr($0,13+index($0, "not found in ")) "/" temp_parts[1];
    print "Creating temporary directory:", dirname;
    system("mkdir \"" dirname "\"");

  }
} 
##End mkdir.mawk contents 
```

Here is the output:
```
temp: \\users\\edmondt\\Temp\\Temp Files\\JSC302E4_edmondt\\JSCf064.tmp" not found in /home/edmondt/.wine/dosdevices/c:/users/edmondt/Temp/Temp Files
temp_len: 65
temp: \\users\\edmondt\\Temp\\Temp Files\\JSC302E4_edmondt\\JSCf064.tmp
temp_parts_qty: 13
Creating temporary directory: /home/edmondt/.wine/dosdevices/c:/users/edmondt/Temp/Temp Files/
mkdir: cannot create directory `/home/edmondt/.wine/dosdevices/c:/users/edmondt/Temp/Temp Files/': File exists

```

What I basically want is to create the directory: "mkdir -p ~/.wine/drive_c/users/edmondt/Temp/Temp\ Files/JSC302E4_edmondt" so that temp files can be created and Enhance Photos and Undo would work within the program.

I can manually mkdir ~/.wine/drive_c/users/edmondt/Temp/Temp\ Files/JSC302E4_edmondt but the pid changes all the time... I can get the pid by 
```
ps ux | awk '/Paint Shop Pro/ && !/awk/ {print $2}'
```

I just need help in putting everything together please, and my ubuntu life would be complete with Paint Shop Pro 9 :)

---

### Post by DaithiF on 2010-06-16
Hi,
I'm quite confused by your post, I don't understand why the awk script if you can get the pid using ps.  Anyway, i've possibly misunderstood what you're trying to do, but if what you are trying to do is (a) launch a command, and (b) create a directory whose path contains the pid of that command (testing first if the directory already exists), then this would do it.  I'm using gedit as an example of a command to run, as i don't have wine or psp installed, and i'm obviously just making up a directorypath, adapt as needed for your requirements.
```
gedit &       # launch some command in the background
pid=$(pidof gedit)  # get the pid of that command
[[ -d "/home/dave/tmp/dir${pid}" ]] && { echo "Directory already exists"; } || { echo "Directory does not exist, creating it now..."; mkdir -p "/home/dave/tmp/dir${pid}"; }  # if the directory ~/tmp/dir<pid> exists then do nothing, otherwise create it

```

---

### Post by edmondt on 2010-06-16
Just want to share my progress...running wine-1.2-rc3, doesn't quite work... Maybe a lower version wold be better...
```


env WINEPREFIX="/home/edmondt/.wine" wine C:\\windows\\command\\start.exe /Unix /home/edmondt/.wine/dosdevices/c:/users/edmondt/Start\ Menu/Programs/Jasc\ Software/Jasc\ Paint\ Shop\ Pro\ 9.lnk

PSPPID=$(ps -eo pid,args | grep Paint\ Shop\ Pro | grep -v grep | cut -c1-6)
PSPPID_TRIMMED=$(echo $PSPPID | tr ' ' _ | tr \" ' ')

chmod ugo=+rwx ~/.wine/drive_c/users/edmondt/Temp/Temp\ Files
mkdir -p ~/.wine/drive_c/users/edmondt/Temp/Temp\ Files/JSC"$PSPPID_TRIMMED"_edmondt
chmod ugo=+rwx ~/.wine/drive_c/users/edmondt/Temp/Temp\ Files/JSC"$PSPPID_TRIMMED"_edmondt


```

Anyway...I'm going to let this one go... Linux really needs a better alternatives than GIMP, or running Photoshop with wine :(

Paint Shop Pro (now PaintShop Photo X3) is a Inkscape mixed with GIMP... I really miss the Enhance Photo feature, makes it easy to re-light the photos and remove digital camera noise and other fix ups...

We need to replace Evolution Mail Client really badly, I tried Claws Mail which is faster... Evolution  is horrible with IMAP, and Exchange 2007 support is terrible, mapi plugin doesn't work... now running DavMail to connect to Exchange 2007 as a quick fix for now...

Ubuntu is strong, but the apps are really....really weak...

---

### Post by asdfoo on 2010-06-17
> **edmondt said:**
> Just want to share my progress...running wine-1.2-rc3, doesn't quite work... 

what do you mean "doesn't quite work", what happens? does it crash? does it start? does it run but particular features don't work?

The command you're using to start the program is a little strange, you should really just cd to the install directory and start the main executable.

---

### Post by js31 on 2010-10-27
I guess it's not so far from a solution what you created. I tried with PSP8/wine-1.2 (username/PSP "JS" in capslock, despite Profile)

```
env WINEPREFIX="/home/js/.wine" wine C:\\windows\\command\\start.exe /Unix /home/js/.wine/dosdevices/c:/users/js/Start\ Menu/Programs/Jasc\ Software/Jasc\ Paint\ Shop\ Pro\ 8.lnk
PSPPID=$(ps -eo pid,args | grep Paint\ Shop\ Pro | grep -v grep | cut -c1-6)
PSPPID_TRIMMED=$(echo $PSPPID | tr ' ' _ | tr \" ' ')
chmod ugo=+rwx ~/.wine/drive_c/users/js/Temp/Temp\ Files
mkdir -p ~/.wine/drive_c/users/js/Temp/Temp\ Files/JSC"$PSPPID_TRIMMED"_JS
chmod ugo=+rwx ~/.wine/drive_c/users/js/Temp/Temp\ Files/JSC"$PSPPID_TRIMMED"_JS
```

and got this error code when running the above as psp8.sh (filters then don't work):
```
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:exec:SHELL_execute flags ignored: 0x00004100
```

Could someone please help? <3

---

### Post by lykeion on 2010-10-27
You should read the additional comments on this page:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2505](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2505)

And btw I find GIMP superior to PSP when it comes to enhancing photos.
[http://docs.gimp.org/en/gimp-imaging-photos.html](http://docs.gimp.org/en/gimp-imaging-photos.html)

---

### Post by js31 on 2010-10-27
I've also tried this tutorial, just with paths/program name according to version 8:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2505&iTestingId=35124](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2505&iTestingId=35124)

Seems the workaround itself only applies to certain versions of PSP8+? I got the original 8.00. Wine 1.0.1 crashes PSP. I give up, too. ](*,)


@lykeion our replies overlapped :popcorn:
Thanks! Something I missed out -> the only Wine version I haven't tested/1.1.42 (as WineHQ pulled the Jaunty-binary) seems to work? I leave that open for Friday when my system will be set up from scratch.

---

### Post by lykeion on 2010-10-27
I meant the additional comment, not the script tutorial:

PSP9 cannot create temp file folder for the filters and undo. Once you create manually the required folder, these features work fine.
 
There is no need for complex startup-script. The folder is created under "Temp Files" (see PSP's Preferences->File Locations ...) and its name consists of JSC + five numbers + _username, eg. JSC82997_arnie. The number part varies between installations, but stays same between program runs.

You can find the folder name for example using 'strace'. At first find PSP's PID with ps -e | grep Paint (or System Monitor, if being on Ubuntu). Then run strace -p  2>&1 | grep "JSC" and start drawing something. You should see some garbage from where you could parse the correct path, eg:
/home/arnie/.wine/dosdevices/c:/windows/temp/Temp Files/JSC82997_arnie/

---

### Post by js31 on 2010-10-27
I tried that, tonight, but the garbage wasn't useable, just something like repeatedly:
```
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [HUP INT USR1 USR2 ALRM CHLD IO], [], 8) = 0
mmap2(0x57e0000, 4096, PROT_NONE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS|MAP_NORESERVE, -1, 0) = 0x57e0000
```

And I agree, Gimp is much more powerful. The reasons why I considered PSP was simple automation, export/file handling and crop tool for big selections like screenshots on small screens (slow ruckling scrollbars when drawing the crop lines!), plus the standard theme. Since Inkscape has blur functionality, one feels kind of tempted to give up photo editing, but that's unrealistic of course, so back to the hybrides, etc. Wished Gimp were available as Inkscape-plugin lol.

---

### Post by lykeion on 2010-10-27
Ok, I can't help you further without trying with PSP + wine myself.
But I can recommend you to install gimp-plugin-registry. It's a lot of extra plugins for Gimp which are really useful, like batch processing and save-for-web.

---

### Post by js31 on 2010-10-27
Thanks for looking into this! =)

And, wow, plugin registry's real mighty! <3 I guess you're right, PSP8+ under Wine seems a bit ressource-consuming, anyway.

---

