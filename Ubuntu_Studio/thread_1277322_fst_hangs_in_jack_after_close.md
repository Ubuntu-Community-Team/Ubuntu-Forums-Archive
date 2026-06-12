---
title: "fst hangs in jack after close"
date: 2009-09-28
forum: Ubuntu Studio
---

### Post by c00kie55 on 2009-09-28
sorry if this is noob.
when compiled fst from git no errors
its starts fine and i can make projects with lash-panel, glasctl or patchage its cool but when i close a project vst plugs hangs in jack so i have to restart jack this dosent happend if i close my vst's before closing lash project and this only happends with vst plugs

the error code in lash is fixme:event:wait_for_withdrawn_state window 0x10038/5c00005 wait timed out

btw iam running ubuntu desktop karmic with ubuntu studio on top
but i get same error in clean karmic desktop, ubuntustudio 9.4 and 64studio 3 grrr 
does anyone know how i can fix it thanX in advance

---

### Post by Stochastic on 2009-09-28
Sounds to me like it's a consistent issue that you should tell the fst developers about.

---

### Post by c00kie55 on 2009-09-29
thanx    	Stochastic

i just compiled lash 0.6 and ladi patchage installed wine1.2 recompiled fst still the same
and i now have to compile everything against lash 0.6 (hydrogen, calf, jack-rack and so one) to get it working with lash is there a way telling apt-get to use my build lash insted of the one in repro 
 



is there a forum for fst help anywhere or is it all irc guess i need a good irc client then (with a gui ) does anybody know one

---

### Post by thorgal on 2009-09-29
you can try kvirc

[http://www.kvirc.net/](http://www.kvirc.net/)

there should be a package in the repos.

---

### Post by c00kie55 on 2009-09-29
it looks like what i was looking for i will give it a go thanx

---

### Post by c00kie55 on 2009-09-29
well it looks like i found a work-around myself  hehe iam so happy.. with the new wine i just told it to emulate windows 2000 it worked 2 times in a row gonna try some more later

---

### Post by c00kie55 on 2009-09-29
back to old error guess i was lucky or blind grrr

---

### Post by c00kie55 on 2009-09-29
[13:26:13] Attempting connection to lad.freenode.net (Freenode) on port 6667
[13:26:13] Looking up the server hostname (lad.freenode.net)...
[13:26:13] Can't find the server IP address: Valid name but the host has no IP address
[13:26:13] If this server is an IPv6 one, try /server -i lad.freenode.net
[13:26:13] Connection attempt failed [lad.freenode.net]

or 

[13:30:29] Attempting connection to ardour.freenode.net (Standalone Servers) on port 6667
[13:30:29] Looking up the server hostname (ardour.freenode.net)...
[13:30:29] Can't find the server IP address: Valid name but the host has no IP address
[13:30:29] If this server is an IPv6 one, try /server -i ardour.freenode.net
[13:30:29] Connection attempt failed [ardour.freenode.net]
[13:30:29] Will attempt to reconnect in 10 seconds [3 of 15]

anywhere else to get support or iam i misstyping the url
i tryed with fst 1.8 and i got lots of errors compiling but it dosent seams to hang in jack 
guess i dosent like wine 1.2 from karmic repro

---

### Post by c00kie55 on 2009-09-29
just compiled 1.8 as in here [http://ubuntuforums.org/showthread.php?t=557466](http://ubuntuforums.org/showthread.php?t=557466) without errors but now it hangs again

---

### Post by c00kie55 on 2009-09-29
it was becource i somehow installed liblash2 5.4 after removing again the errors are

~/fst$ make
cp -a `find . | grep 'vstsdk[^/]*\$'`/source/common ./vst
sed -i '/struct VstFileType\|struct VstFileSelect/,/};/d' vst/aeffectx.h
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o audiomaster.o audiomaster.c
audiomaster.c: In function ‘jack_host_callback’:
audiomaster.c:119: warning: incompatible implicit declaration of built-in function ‘floor’
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o fst.o fst.c
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o fstinfofile.o fstinfofile.c
fstinfofile.c: In function ‘load_fst_info_file’:
fstinfofile.c:36: warning: incompatible implicit declaration of built-in function ‘malloc’
fstinfofile.c:47: warning: incompatible implicit declaration of built-in function ‘free’
fstinfofile.c:76: warning: incompatible implicit declaration of built-in function ‘free’
fstinfofile.c: In function ‘fst_info_file_is_valid’:
fstinfofile.c:139: warning: incompatible implicit declaration of built-in function ‘free’
fstinfofile.c: In function ‘fst_info_from_plugin’:
fstinfofile.c:162: warning: incompatible implicit declaration of built-in function ‘malloc’
fstinfofile.c: In function ‘fst_get_info’:
fstinfofile.c:220: warning: incompatible implicit declaration of built-in function ‘free’
fstinfofile.c:246: warning: incompatible implicit declaration of built-in function ‘free’
fstinfofile.c: In function ‘fst_free_info’:
fstinfofile.c:258: warning: incompatible implicit declaration of built-in function ‘free’
fstinfofile.c:261: warning: incompatible implicit declaration of built-in function ‘free’
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o gtk.o gtk.c
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o jfst.o jfst.c
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o vsti.o vsti.c
vsti.c: In function ‘queue_midi’:
vsti.c:79: warning: assignment from incompatible pointer type
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o vstwin.o vstwin.c
vstwin.c: In function ‘fst_load’:
vstwin.c:480: warning: assignment from incompatible pointer type
winegcc -mwindows -o fst.exe audiomaster.o fst.o fstinfofile.o gtk.o jfst.o vsti.o vstwin.o     `pkg-config --libs gtk+-2.0` `pkg-config --libs jack` `pkg-config --libs alsa` `pkg-config --libs lash-1.0`  -L/usr/X11R6/lib -lX11   -luuid


guess this aint real errors ?? [http://ubuntuforums.org/showthread.php?t=1251732](http://ubuntuforums.org/showthread.php?t=1251732)

---

### Post by c00kie55 on 2009-09-29
it dosent hang now but i cant save


hmm seams to be becourse i didnt do this 
<TheMuso> Open the Makefile in an editor, and look for the line starting with LIBRARIES
<TheMuso> Its right under LIBRARY_PATH
<TheMuso> At the end of that line, right after -lX11, add a space, followed by -lpthread
<TheMuso> Save the file 			 		

now my error is it dossent auto connect in patchage 
Unable to find port to connect
Unable to create port view
Unable to find port to destroy
 
guess the error now is in patchage

---

### Post by c00kie55 on 2009-09-30
can someone point out for me where i can get support for fst  lad.freenode.net don't seams to work old or am i plain stupid maybe my irc client is playing with me. and isn't it dangerus to be on freenode (hachers and scriptkidyes) aint there a forum somewhere

anyway it still hangs and now iam having truble making fst 1.8 i think it migth be some old. wine left overs or somthing migth have chansed

---

### Post by Stochastic on 2009-10-01
go to irc.freenode.net and room/channel #lad (no it's not dangerous to be on freenonde).

Oh, and it's kinda strange to talk to yourself so much in a forum environment (hopefully you don't do it in real life too ;).

---

### Post by c00kie55 on 2009-10-01
i do all the time ?? guess im new on linux dohh and wanna lean and get moving course have been figthing that fst sometime dont you never talk to youself (even in trubles time)
really its not nice pointing out that iam maniac \\:D/you know specialy not in a forum like this ? i have been on freenode looking for lad with kvirc that i installed from repro but i dont think it was working?? when moving in places like mirc i have always thougth [I]security was inportent and i dont know 4sure that all my ports are clossed but nevermind that  

and really i was just trying to point out the kind of errors i got and the prosses moving
maybe someone else have been there guess you havent 

i remember i once had fst 1.8 working but i cant get back now it compile with errors 
(guss iam i talking to my self again) iam i ?

my biggst prob is now that i have tryed how it can work on linux i dont wanna go to windows even thoe i can get most of the apps working there running trough jack i still miss fst, jost, lash, hydrogen and probely somthing else...
 
i would like to have this notebook working like a rack server it could be cool
yes i allready got it working on windows but i like free things.. and windows feels so clossed. by the way i just saw jvstwraper have anyone tryed that i thougth i migth work as a host even that it is not the point maybe someone else who talk to him or her self .. guess i dont care looking folish just wanna have the best audio envioment bla bla 
 
[/I]

---

### Post by c00kie55 on 2009-10-04
just tryed in  clean hardy and guess what.. same hang error yeap. iam starting to think this just aint working in ubuntu yet.. also i have been on #lad and the guys i talked to there cut not help.. _**Anyone got this working**_ (if you dont use lash you probely think everthing is working but..)  


from terminal try to start a lash_panel make a project including a vsti(fst ofcourse) close the project not the vsti and i bet you got fixme wait error 
if not i must have a hardware issue 

cut someone try this and report back please...

---

