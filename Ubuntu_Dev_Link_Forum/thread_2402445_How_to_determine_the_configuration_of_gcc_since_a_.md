---
title: "How to determine the configuration of gcc since a bash script?"
date: 2018-09-30
forum: Ubuntu Dev Link Forum
---

### Post by fnuxfl on 2018-09-30
Hello,

I have a bash script that compiles a program as well on older versions of Ubuntu (14.04 and 16.04) than on the last one (18.04) as well as on other distributions and therefore with different gcc settings.

To obtain an executable that can be launched (among other things) by a double click, I compile this program without the "-no-pie" option with older versions of gcc when I have to use this option for the new version (gcc 7.3 and higher).

The problem is that with the new configuration of gcc having the option "--enable-default-pie" of the last version of gcc, if I compile my program without the option "-no-pie", the result is an executable which is of the shared library type which can not be launched by a double click.

My question is either:

a) Is there a command that allows me to determine from this bash script if gcc is configured with the "--enable-default-pie" setting?

b) or if not, is there a command that allows me to determine from this bash script if the compiled file is of the shared library or executable type?

If I do not find an answer to my first option, the second (it is true less elegant but just as effective) would allow me to compile first without the "-no-pie" option and if the result is a shared library, of restart this compilation this time with the option "-no-pie" for, in one case as in the other, get an executable that can be launched by a double click whatever the setting of gcc.

Thank you in advance for your ideas and suggestions.

Best regards.

---

### Post by fnuxfl on 2018-10-01
Hi all (again),

Let's go to the second option (b) of my requets above where I'm looking for a command that displays a file type.

When uszing Xubuntu, 18.4.1, the Fle Manager displays on the bottom line of its window the file type.

e.g.

Below is the result of a .cpp source file compiled with g++ and the option "-no-pie" that the File Manager displays as "**executable**".

[IMG]http://www.as2.com/pictures/png/test-1-us.png[/IMG]

Then below is the result of the exact same .cpp source file but now compiled with g++ and **without** the option "no-pie" and that the File Manager now displays as "**shared library**".

[IMG]http://www.as2.com/pictures/png/test-2-us.png[/IMG]

So, my question is what is the command to use in a terminal (and the reply to expect) to get such a file type (**executable** or **shared library**)?

Please help me.

TIA for your time and suggestions.

Best regards.

---

### Post by steeldriver on 2018-10-02
The command-line tool to detect file type is `file` e.g.

```

$ file hello
hello: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 2.6.32, BuildID[sha1]=5ef2c56f72d777c753846d70aa6ef7ef7ec13c86, not stripped

```

Not sure the best way to see gcc build-time configuration settings but you could try

```

gcc -dumpspecs

```

---

### Post by fnuxfl on 2018-10-02
Hi steeldriver,

Thank you so much for your time and interest.

OK, the "file myprogram" command displays he following response:

$ file myprogram
myprogram: ELF 64-bit LSB executable, x86-64, version .............

However, I'm a complete and [COLOR=#222222][FONT=Verdana]unfortunately i[/FONT][/COLOR]gnorant newbee with the grep and sed commands yet.

So, could you please show me with a command line sample how to check if the word "executale" is in the response provided with the "file" command that I could assign to a variable and use in my bash script?

This would help me a lot [COLOR=#222222][FONT=Verdana]both to learn how to use these commands and to solve my problem[/FONT][/COLOR].

e.g. I got from another bash champion a sample command to check if the gcc compiler uses the --enable-default-pie option with Debian and Ubuntu with the Following command line:

$ if [ -n "`gcc -v -E 2>&1 | grep 'Configured with' | sed 's/--/\n--/g' | grep enable-default-pie`" ]; then echo "PIE DEFAULT"; else echo "PIE NOT DEFAULT"; fi

[LEFT][COLOR=#222222][FONT=Verdana][LEFT][COLOR=#222222][FONT=Verdana]that I translated like this in my script:[/FONT][/COLOR][/LEFT]
------------------------------------------[/FONT][/COLOR][/LEFT]
check_gcc()
{
    if [ -n "`gcc -v -E 2>&1 | grep 'Configured with' | sed 's/--/\n--/g' | grep enable-default-pie`" ]
        then
            GCC_SETTING="1"
        else
            GCC_SETTING="0"
    fi
  read -p "The gcc setting is $GCC_SETTING " GCCRESULT
}
[LEFT][COLOR=#222222][FONT=Verdana]#[/FONT][/COLOR][/LEFT]
# Then I deal with the $GCC_SETTING value.
[LEFT][COLOR=#222222][FONT=Verdana][LEFT][COLOR=#222222][FONT=Verdana]# [/FONT][/COLOR][/LEFT]
------------------------------------------[/FONT][/COLOR][/LEFT]

Once again, thank you very much for your time and interest.

Best regards.

---

### Post by steeldriver on 2018-10-02
The `file` utility has a number of options that may be useful for getting more easily parsable output - for example you could do

```

$ file --brief --mime-type hello.o hello
application/x-object
application/x-executable

```

and then test for the string `application/x-executable`

However I don't really understand what you are trying to do - can't you just use the flags you want on either system? For example, with either gcc-5 (default no-pie) or gcc-7 (default pie):

```

$ gcc-5 -o hello -fpic -pie hello.c
$ file --brief --mime-type hello
application/x-sharedlib
$
$ gcc-5 -o hello -fno-pic -no-pie hello.c
$ file --brief --mime-type hello
application/x-executable

``````

$ gcc-7 -o hello -fpic -pie hello.c
$ file --brief --mime-type hello
application/x-sharedlib
$
$ gcc-7 -o hello -fno-pic -no-pie hello.c
$ file --brief --mime-type hello
application/x-executable

```

---

### Post by fnuxfl on 2018-10-03
Hi steeldriver,

Once again, thank you very much for your clear explanation since I didn't know the $`file` options.

> **steeldriver said:**
> The `file` utility has a number of options that may be useful for getting more easily parsable output - for example you could do

```

$ file --brief --mime-type hello.o hello
application/x-object
application/x-executable

```

and then test for the string `application/x-executable`


Thanks to your information, this is how I solved my problem:

```

# test the compiled file type
#
check_type()
{
    FILE_TYPE=$(file -b --mime-type $FILETOTEST)
    if [ $(file -b --mime-type $FILETOTEST) = "application/x-executable" ]
        then
            FILE_MIME="1"
        else
            FILE_MIME="0"
    fi
  echo "The $FILETOTEST type is $FILE_TYPE and the mime type is $FILE_MIME ! "
}
FILETOTEST="myprog"
check_type $FILETOTEST
``` 

Then I deal with the response to adapt the gcc compilation option.

> **steeldriver said:**
> However I don't rallye understand what you are trying to do - can't you  just use the flags you want on either system? For example, with either  gcc-5 (default no-pie) or gcc-7 (default pie):

In fact, I try my best to polish a bash script that downloads, compiles and installs a set of 3 progams on different Linux systems. So, since I don't know in advance what the distribution may be (e.g. Arch, CentOS, Debian, Fedora, etc.) nor even its version (e.g. Ubuntu 14.04.5 or 16.04.5 or 18.04.1) I need to check what the compiled program type is in order to adapt the compiler option (e.g. using the --no-pie flag or not) accordingly to the gcc setting that depends of each distribution and their different releases (e.g. Ubuntu 16.04.5 Vs Ubuntu 18.04.1).

My multi languages bash script (only in English, French, German, Portuguese and Russian for now) isn't a secret since it proposes to "**Old Dos Lovers**" to install on their Linux system **QB64**, a realy funny cross-platform (Linux, OS/X and Windows) open source BASIC IDE (editor and compiler) almost 100 per 100 compatible with the good old QB 4.5 and its two main open source add-ons: **InForm** being an excellent event driven graphical development environment to create dynamic forms and **vWATCH** being a real-time debugger.

The goal of QB64 is to translate the BASIC .bas source files in C++, then to compile the .cpp translated files to create executables. Then, it's fun to run old basic programs and games from the 80ies on modern Systems (nostalgia). :biggrin:

You can get and take a look at my script here: [http://www.as2.com](http://www.as2.com)

I started this personnal chalenge (this development) almost 2 years ago to learn a little bit the bash language (thank you to a lot of contributors from different forum who are named in the head of the script) and I had to adapt (enhance) it several times to match new distributions and/or new versions.

BTW, I know that I still have to make some changes (especially for Fedora) using my new function but this requests a lot of time, switching form a VM to another to make the relevant tests (i.e. the joy of development, isn't it ?). ](*,) :p

So don't hesitate to send me your critics.

Once again, thank you so much for your time and concerns.

Best regards.

---

### Post by spjackson on 2018-10-03
> **fnuxfl said:**
> 
```

    if [ $(file -b --mime-type $FILETOTEST) = "application/x-executable" ]

``` 

This might work for your build script, but there are platforms on which some ELF executables may give unexpected results. e.g.
```

$ uname -a
Linux u18-04-desktop 4.15.0-36-generic #39-Ubuntu SMP Mon Sep 24 16:19:09 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
$ file -b --mime-type /bin/cat
application/x-sharedlib

```

---

### Post by fnuxfl on 2018-10-04
Hi sjackson,

Thank you for your post.

This was exactly the goal of my questions since my script is supposed to work both with ubuntu 14.04 and 16.04 as well as with the last 18.04 (I use only LTS)and alos on other distros such as Debian, LMDE, Mint or even CentOS and Mangaro (that is my chalenge).

Or, as you know, the gcc settings have been changed between the previous Ubuntu releases (no-pie) and the last one (enable-default-pie).

Then, when compiling my program on the 18.04 without the -no-pie argument, I got an "executable" of the type "shared library" that you could launch using the classic ./myprogram or any starter but not with a left double click on its icon (just anoying).

However, compiling the same myprogram with the -no-pie argument on the 18.04 fixes it.

Now, i know that the gcc compilation command line using the -no-pie argument on CentOS (or Fedora and I guess on RedHat too) isn't recognized on these distros (I tried unsuccessfully).

Anyone knowing how to change the gcc setting on CentOS 7.5.1804 within the compilation command line would help me tremandously (Amazingly, I don't need it on CentOS 7.2.1511 since my original compilation command line works fine and that the compiler is the same "4.8.5 20150623 (Red Hat 4.8.5-28)". Further, the "gcc -v" command responds exactly the same thing on these two different CentOS releases. Funy isn't it ?). ](*,)

Thank you again for your time and concern.

Best regards.

---

