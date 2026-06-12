---
title: "Compiling"
date: 2015-01-02
forum: Ubuntu/Debian BASED
---

### Post by FATALERROR0x0x on 2015-01-02
Hello guys,

its been 3 days and now its really frustrating me.  I wanted to compile a program called hla(high level assembly). a piece a of software for a tutorial  but i just cant install it on my distro.  i use kali linux but i want to install the program on puppy linux.  

here is the linux to the program:
[http://www.plantation-productions.com/Webster/HighLevelAsm/dnld.html](http://www.plantation-productions.com/Webster/HighLevelAsm/dnld.html)

please i really need help.
thank you.

---

### Post by schragge on 2015-01-02
What is your problem exactly? What errors do you get trying to compile hla?

BTW, the site you linked above also offers pre-compiled statically-linked binaries of hla together with installation instructions. Are you sure you absolutely need to compile hla from source? Have you tried to run it as is?

Besides, questions about compiling programs on Puppy are best answered at either [http://www.murga-linux.com/puppy](http://www.murga-linux.com/puppy) or [http://puppylinux.info](http://puppylinux.info)  Puppy is a very peculiar distribution. It has several flavours, e.g. IIRC one variant of it is built from Ubuntu packages (Tahrpup), another from Slackware packages (Slacko), but even Tahrpup actually has very little in common with Trusty Tahr beside software being at the same versions. It uses neither dpkg nor APT and has quite different distribution infrastructure and philosophy.

---

### Post by FATALERROR0x0x on 2015-01-02
Thnxx for the reply brother
              So you are saying that they are pre-compiled so there is no need to compile it.  But i see a makefile.  The thing is that i can run the hla program with this command
./hla after changing directory.  But when i run the program to compile the code, we need to add another program to the system variable and stuff.  Please man  Can you just give me a step by step install procedure.

let me tell you what i did:
i downloaded the linux.hla.tar.gz

then extracted it 
then cd to the directory where the hla executables are
there is a makefile but tried to make it several times but in vain
after several times of deletion and extraction i decided not to makefile with make
so i launched the program manually,   ./hla
the program worked
but when i wrote my code and saved it as hw.hla and tried to compile it by using 
./hla -v hw
this is the error i get
could not locate hlalib.a file.  Have you set the 'hlalib' environment variable properly?
and this is where am stuck.

please help me man

---

### Post by schragge on 2015-01-02
The makefile there is for source distibution. The package you downloaded is binary distribution. All information about environment variables, installation procedure and so on is on the site you linked above, directly under download links for linux packages.

---

### Post by FATALERROR0x0x on 2015-01-02
Sir, i decided to INSTALL hla on kali linux.  all is working well but i wanted to use linux in vmware inside windows.  THANKS A LOT FOR EVRYTHING SIR.  BTW HAPPY NEW YEAR 2015.  MAY THIS YEAR BRING YOU LOTS OF HAPPINESS!!

---

### Post by howefield on 2015-01-02
Thread moved.

---

