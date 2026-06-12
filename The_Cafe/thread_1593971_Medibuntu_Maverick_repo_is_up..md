---
title: "Medibuntu Maverick repo is up."
date: 2010-10-11
forum: The Cafe
---

### Post by alphacrucis2 on 2010-10-11
No googleearth yet though.

---

### Post by Lenny212 on 2010-10-13
hmmm...how long until googleearth is available and how do we know when it becomes available

---

### Post by alphacrucis2 on 2010-10-13
> **Lenny212 said:**
> hmmm...how long until googleearth is available and how do we know when it becomes available

Here are the Maverick packages they have:

[http://packages.medibuntu.org/maverick/index.html]("http://packages.medibuntu.org/maverick/index.html")

As to when googleearth will be available there I don't know.

---

### Post by NightwishFan on 2010-10-13
You can build google earth deb for yourself. (Very easy). Install this package: [http://packages.ubuntu.com/maverick/googleearth-package](http://packages.ubuntu.com/maverick/googleearth-package)

You can either click: [_[COLOR="Blue"]Install googleearth-package[/COLOR]_]("apt://googleearth-package") or run this command to install.
```
sudo apt-get install googleearth-package
```

Then just run this to figure it out:
```
man googleearth-package
```

---

### Post by alphacrucis2 on 2010-10-13
> **NightwishFan said:**
> You can build google earth deb for yourself. (Very easy). Install this package: [http://packages.ubuntu.com/maverick/googleearth-package](http://packages.ubuntu.com/maverick/googleearth-package)

You can either click: [_[COLOR="Blue"]Install googleearth-package[/COLOR]_]("apt://googleearth-package") or run this command to install.
```
sudo apt-get install googleearth-package
```

Then just run this to figure it out:
```
man googleearth-package
```

Already did that. Crash signal 6 immediately after the googleearth splash screen appears. Same deal with the latest download direct from google. I'm hoping medibuntu might work some magic with their version but I have a horrible feeling that the AMD blob (Catalyst 10.10) is the cause. Trouble is I can't live without the GPU power management that the blob gives me on my laptop.

---

### Post by NightwishFan on 2010-10-13
Edit: man googleearth-package might not be the right command. I am surprised it does not work for you though. Might be gpu releated I will try it on mine.

Edit edit: it is "man make-googleearth-package"

Edit edit edit: From the man page. You can use make-googleearth-package to install an older version I believe.
> --file file
              Use file instead of GoogleEarthLinux.bin

--force
              Attempt to build an unsupported version

---

### Post by alphacrucis2 on 2010-10-13
Yeah. You run make and then install the deb. Doesn't matter which method I use, I get a crashlog like this:

```
Crash Signal 6
Crash Time 1286798958
Up Time 0.393897

Stacktrace from glibc:
./libgoogleearth_free.so(+0xd090b)[0xf771790b]
[0xf7770400]
/lib32/libc.so.6(abort+0x182)[0xf5a47e42]
/lib32/libc.so.6(__assert_fail+0xf8)[0xf5a3d878]
/usr/lib32/libX11.so.6(_XReply+0x352)[0xf4e75282]
/usr/lib32/libGL.so.1([COLOR="Red"]AtiCallFGLComposite[/COLOR]+0xf5)[0xf4d8588b]
```

Maybe I will deinstall the blob and try the OSS driver as a test.

---

### Post by NightwishFan on 2010-10-13
Just tested this myself and it works fine. It says "unsupported version of google earth, try using force" I did so and the deb installs and performs well. Note I used the google earth that the program downloaded not a custom one. Perhaps it is a new error due to Xorg 1.9 and your graphics drivers. Try researching parts of the error output.

---

### Post by alphacrucis2 on 2010-10-13
> **NightwishFan said:**
> Just tested this myself and it works fine. It says "unsupported version of google earth, try using force" I did so and the deb installs and performs well. Note I used the google earth that the program downloaded not a custom one. Perhaps it is a new error due to Xorg 1.9 and your graphics drivers. Try researching parts of the error output.

No joy for me. I eliminated fglrx and OpenGL is now being provided by Mesa. Now googleearth doesn't crash but I get this instead:

laptop:~$ googleearth
/usr/lib/googleearth/googleearth-bin: error while loading shared libraries: libatiuki.so.1: cannot open shared object file: No such file or directory.

---

### Post by NightwishFan on 2010-10-13
That is getting closer. You might just need to reinstall GE from the bin file or make a new package.

---

### Post by alphacrucis2 on 2010-10-13
> **NightwishFan said:**
> That is getting closer. You might just need to reinstall GE from the bin file or make a new package.

Yeah. I wondered about that. I removed googleearth via apt-get and then did the make-googleearth-package --force bit and installed the resulting deb. Back to the original signal 6 crash :confused:. So it looks like fglrx is in the clear on this one so I have reinstalled it. The only other thing I can think of is that I am running 64 bit and it looks like googleearth is a 32 bit app. I am running some other OpenGL apps that are working perfectly but they are proper 64 bit apps.

---

### Post by NightwishFan on 2010-10-13
I am running 64-bit as well, though that might be part of it. Do you have ia32-libs installed? Though I doubt that will help.

---

### Post by alphacrucis2 on 2010-10-13
> **NightwishFan said:**
> I am running 64-bit as well, though that might be part of it. Do you have ia32-libs installed? Though I doubt that will help.


Yeah I do. I just tried reinstalling it but no help. Ah well.

---

### Post by DougieFresh4U on 2010-10-13
I installed the Lucid GE in my Maverick install and all went well on my 64bit ATI Radeon HD3200

---

### Post by alphacrucis2 on 2010-10-13
> **DougieFresh4U said:**
> I installed the Lucid GE and all went well on my 64bit ATI Radeon HD3200

Yeah it used to work for me on Lucid 64 too. Not sure exactly what is causing it yet.

---

### Post by scouser73 on 2010-10-13
I installed the Lucid version of Google Earth on Maverick from the Medibuntu site and have had no problems.

---

### Post by alphacrucis2 on 2010-10-13
Well is looks like the problem I am having is something to do with the version of the ia32-libs I have installed. I tried installing a much newer version from the debian repos and that fixed googleearth but broke skype so I have backed out to the Ubuntu one. Oh for all native 64 bit apps.

---

### Post by Lenny212 on 2010-10-14
I am running 32bit Maverick and installed the Lucid version and it worked.
Click [here]("http://packages.medibuntu.org/pool/non-free/g/googleearth/googleearth_5.1.3533.1731-0medibuntu1_i386.deb") and it will download the .deb file for you.
You then double click the file to install.

---

### Post by disastrophe on 2010-10-14
I ran the make and two thirds of the output was dependency warnings. I suspect I have one nasty little deb setting there so I sent it to the round file cabinet. No biggie I guess, I already have it installed on Squeeze anyway.(PCLOS too I think) But as soon as I ran the make I was like WTF?

---

### Post by cg0191 on 2010-10-15
Thanks for the info.
Can someone explain if this is still necessary when one has elected to click the checkbox to install multimedia support during the 10.10 (Meerkat) install.

Do I already have libdvdcss2 & all the codecs already or not??
This is so typically 'Linuxish'... Dear god could someone bother to document things properly for a change???

---

### Post by NightwishFan on 2010-10-15
It is documented. Libdvdcss will likely never be included in the Ubuntu repos due to legal issues. You can simply run this command to install libdvdcss:
```
sudo sh '/usr/share/doc/libdvdread4/install-css.sh'
```

Much of the other stuff in Medibuntu I would never need, you can judge if you do or not.

---

### Post by hneto on 2010-10-16
Definitely no more googleearth from Medibuntu:

[https://launchpad.net/medibuntu/+announcement/6939](https://launchpad.net/medibuntu/+announcement/6939)

---

### Post by thewolfman on 2010-10-16
Hi chaps, I didn't read every post in this thread but I am having a problem with the "Public Key", I keep getting the message that it isn't available. Anyone having the same problem?????.

Thanks in advance.:(

---

