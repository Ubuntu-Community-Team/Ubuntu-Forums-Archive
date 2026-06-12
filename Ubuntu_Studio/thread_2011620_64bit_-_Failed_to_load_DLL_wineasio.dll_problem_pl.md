---
title: "64bit - Failed to load DLL wineasio.dll *problem please help*"
date: 2012-06-27
forum: Ubuntu Studio
---

### Post by studiofreak on 2012-06-27
*/its defiantly ubuntu studio 64bit/*
 
using wineasio install version: wineasio_0.7.5_64bit.deb 

(if anyone has .deb 64bit version of 0.8 or 0.9 if there are any can you please point me to one to update it?)


terminal with no sudo: 

regsvr32 wineasio.dll

*/returns/*

Failed to load DLL wineasio.dll

------------------------------------------------------------------

all the wineasio.dll's are in the following after install: (copying the directory from the address bar as I have enabled that in nautilus setting the boolean to true)

/usr/lib/wine/wineasio.dll.so
/usr/lib/x86_64-linux-gnu/wine/wineasio.dll.so

/usr/lib32/wine/wineasio.dll.so

------------------------------------------------------------------
the wine install I have is:

wine: 

1.4-0ubuntu4 (32bit and 64bit support installed)
(and the dev version)

winetricks:

0.0+20120308

wine gecko:

1.4-0ubuntu4

gnome wine icon theme:

5.5.1-1ubuntu1




Can anyone help I have done everything in my power to try and make this work?

:mad:

If anyone can help me fix this id be truly very grateful, 

Thanks.

---

### Post by studiofreak on 2012-06-27
OK quick update I converted the : wineasio-0.9.0.tar.gz

to

wineasio_0.9.0-2_all.deb

with alien

:guitar: if anyone wants it that is, I have attached it.


here is the file: [http://www.4shared.com/rar/cpXFTkOu/wine_asio_090-2_deb.html](http://www.4shared.com/rar/cpXFTkOu/wine_asio_090-2_deb.html)

:guitar:

---

### Post by sgx on 2012-06-27
Hi, when you have time, could you look at the
wine registry folder and

HKEY_CURRENT_USER

Software

Wine

Drivers

Winealsa

is the first line set to alsa, jack, default,
or something else? I'm curious to see the value
that comes out of the 12.04 ubuntu wine installation.
Cheers

wine regedit

should open the registry for you.
Cheers

---

### Post by studiofreak on 2012-06-27
all i see is a folder:

winealsa.drv

Containing 3 REG_SZ files, the first one says data and (value not set)

which is the default

default input is the 2nd down with a load of data strings 

default output is the same with data strings

Can you elaborate on what you mean mean to check?

Thanks

---

### Post by studiofreak on 2012-06-28
OK so still need help with this I HAVE to get this running and another friend has ubuntu 64bit working with wine and wineasio!

so its got to work yeah? You would think so lol but no

:(

---

### Post by studiofreak on 2012-06-28
seriously can anyone help im banging my head against a brick wall here?

---

### Post by studiofreak on 2012-06-28
I uninstalled wine then ran:

~$ WINEARCH=win32 winecfg

*/which returned this /*

p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: cannot open shared object file: No such file or directory
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default

---------------------------------------------------------


so i made the files for the keyring:

/usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so:
/usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so:

and then ran again:

~$ WINEARCH=win32 winecfg

*/which returned this /*

p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: file too short
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default

has anyone any ideas what so ever to help me please?

---

### Post by sgx on 2012-06-29
Hi, before wine 1.4xxx, 1.3 and earlier winecfg audio panel allowed you
to choose between jackd and alsa with a tickbox. vst use needs alsa, which confuses new users, who also require jackd to be the sound server, but don't have access to documentation describing the differences.

In the winealsa.drv folder, I would replace the (Default) in the first line, with alsa -without parentheses, shutdown normally, and reboot.

Use a file manager like nautilus or thunar or pcmanfm, to delete
all Magix items, and run the installer again. If it hangs, move its
window, sometimes a requestor is hidden behind the main installer gui.

Cheers

I would also install reaper, in /home/username
so once the kinks get worked out,
you will have a daw that will work.

[http://www.reaper.fm/](http://www.reaper.fm/)

---

### Post by studiofreak on 2012-06-29
OK great!!

Thanks 

I need to know one thing what is "'Magix' items", why are they there and where would i normally find them?

again thanks, ill get there!

---

### Post by studiofreak on 2012-06-29
OK so i started fresh i un installed wine, did a sudo apt-get autoremove and sudo apt-get clean

etc

and then i re installed wine, then none of the programs from before will work, then i installed wineasio all over again and there is no driver folder in wine in programs in wine now?

:(

its getting on my nerves now! i really know it can work because on ubuntu 10.10 i had it working but i felt ubuntu wasnt up to the mark yet, so i waited a few updates and then fully started to switch at 11.10 and been using it the last 6 months

but only now do i need this with wineasio

what can i do to clean the install up of wine and start fresh now?

hope you can help?

thanks again :guitar:

---

### Post by studiofreak on 2012-06-29
OK you mean Magix Video for windows? As I haven't got that I was running notepad++ and google sketchup along with audible audio books manager etc

and now it still doesnt work!

---

### Post by sgx on 2012-06-29
> **studiofreak said:**
> OK great!!

Thanks 

I need to know one thing what is "'Magix' items", why are they there and where would i normally find them?

again thanks, ill get there!
Sorry, got your issues mixed up with someone else, who is trying
to install Magix Music Creator. The coffeee is as weak
as the concentration.

---

### Post by sgx on 2012-06-29
What I have done in the past, was manually delete
all libwine and the wine folder, from /usr/lib
then rename the .wine folder, and reinstall wine using
synaptic. Wine doesn't use windows drivers

But you are using a new release, and are beta testing,
despite any smiley faced corporate labels. There is almost never
a good reason for a linux using recording musician, to
upgrade a working system, because music doesn't sound better
in a new or 64 bit OS, and software is improved in small increments,
not break-throughs.

Because the marriage of your particular hardware to a working linux
is subject to many forces beyond your control, it is even
more important to maintain a working system, regardless of
versions or age.

Using a new wine release (1.4xxx) with a new ubuntu release,
may not work with what you have, so use 11.10. You can
beta test 12.04 later, installed on an external drive.

other options would be install kx studio on top of basic ubuntu,
a thorough customization with some extra wine functionality,
or use a dedicated audio linux. AVLinux and Tango Studio
have users with ubuntu experience.

Cheers

---

### Post by studiofreak on 2012-07-02
OK mate thats what i thought was to install kxstudio in the end to be honest.

ill probs just do a dual boot for studio use on the net dual core pc.

unless you have any ideas upon this situation: which is what happens after i uninstall and clean everything

(i ran) wine regedit 

*/which returned/*

wine: created the configuration directory '/home/jpskelm/.wine'
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:seh:RtlAddFunctionTable 0x61e45620 1 61e40000: stub
fixme:seh:RtlAddFunctionTable 0x61776ba0 1 61700000: stub
fixme:seh:RtlAddFunctionTable 0x64f69540 1 64f40000: stub
fixme:seh:RtlAddFunctionTable 0x622c6620 1 622c0000: stub
fixme:seh:RtlAddFunctionTable 0x6ce47620 1 6ce40000: stub
fixme:seh:RtlAddFunctionTable 0x682d4b20 1 682c0000: stub
fixme:seh:RtlAddFunctionTable 0x638d1dc0 1 63800000: stub
fixme:seh:RtlAddFunctionTable 0x3b6ea0 1 390000: stub
fixme:seh:RtlAddFunctionTable 0x68f5b6a0 1 68f40000: stub
fixme:seh:RtlAddFunctionTable 0x6b431bc0 1 69c40000: stub
fixme:iphlpapi:NotifyAddrChange (Handle 0xdbe2f8, overlapped 0xdbe2c0): stub
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: file too short
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: file too short
fixme:storage:create_storagefile Storage share mode not implemented.
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
err:mscoree:LoadLibraryShim error reading registry key for installroot
fixme:iphlpapi:NotifyAddrChange (Handle 0xe9e8cc, overlapped 0xe9e8b0): stub
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: file too short
wine: configuration in '/home/*my user name*/.wine' has been updated.

-----------------------------------------------------------------

any ideas on this would be appreciated

thanks

---

### Post by studiofreak on 2012-07-02
OK I have made some headway here!!

i did the following over ubuntu studio 64bit with kxstudio upgrade:

doing the following:

Step 3 - Enable the repositories

Login in the terminal with the user credentials you entered during the installation.
Note: You won't get any feedback while entering the password - this is normal (actually a security feature).

When logged in, run these commands to enable the KXStudio repositories:
sudo apt-get update
sudo apt-get install python-software-properties wget
sudo add-apt-repository ppa:kxstudio-team/kxstudio
sudo apt-get update
sudo apt-get install kxstudio-repos
sudo apt-get update

--------------------------------------------------------------

which is the steps to follow on the kx studio site here [http://kxstudio.sourceforge.net/Documentation:Ubuntu:Install](http://kxstudio.sourceforge.net/Documentation:Ubuntu:Install)

WINE ASIO then straight away registered and shows up etc the only thing I cannot do now is get any audio from my m audio delta 10/10lt sound card only the on board but i am VERY nearly there!

Thanks for all the pointers and help people!

:guitar:

---

### Post by sgx on 2012-07-03
Glad things are working. Make sure that once wine is installed
by sudo, that the windows apps themselves are installed by the
normal user, not sudo. Avoid installing extra windows drivers.
Missing .dll files can be dowmloaded and placed in

/home/username/.wine/drive_c/windows/system32

Repository apps can install using the package manager, or dpkg -i
which require sudo.

Cheers

---

### Post by studiofreak on 2012-07-03
Great thanks for the tip there I didn't know that about repository windows programs for wine. I know about wine tricks etc but there is a few issues with things listed like winamp for instance i couldnt get that to work and after updating to 12.0464bit google sketch up would work so ill try again now!

its fully working and m audio delta 10/10 lt is working with envy mixer for specific m audio cards!!!!!

I even have an alesis usb pro drum kit working, it shows in linux automatically and i can use it in wine as well! it shows in qjackctrl also!

fantastic!

Thanks for the pointers everyone! :guitar:

---

### Post by sgx on 2012-07-04
vlc is a fine alternative to winamp, and works with
qjackctl, for an easy overdub, use vlc as a player,
for track1, and route it, along with your drumkit, to timemachine,
for recording. Pause track1 while you make connections. I make a habit
of recoding extra lead-in quiet time, for such connections,
avoiding the pause.

Edit/convert the tm-xxx.w64 file by importing into audacity.

Great to hear your cool modern gear is working!

Cheers

---

