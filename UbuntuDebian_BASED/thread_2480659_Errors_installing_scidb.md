---
title: "Errors installing scidb"
date: 2022-11-05
forum: Ubuntu/Debian BASED
---

### Post by gabaozin on 2022-11-05
Dear all,


I hope you can help me too.


I will also drop an email to gcramer@users.sourceforge.net.


I am also trying to install Scidb and getting errors. 


I'm running the following linux distro, version and kernel:
Distributor ID:	Zorin
Description:	Zorin OS 16.2
Release:	16
Codename:	focal


Linux 5.15.0-52-generic #58~20.04.1-Ubuntu SMP Thu Oct 13 13:09:46 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux


And here is the output of ./configure and make:


```
./configure: Makefile configuration program for Scidb
Renaming "Makefile.in" to "Makefile.in.bak"
    Tcl/Tk version: 8.6
    Your operating system is: Linux 5.15.0-52-generic
                 Distributor: Zorin OS
                    Revision: 16
                     Version: 16.2
    Checking if your system has gcc installed: yes (version 9.4).
    Checking if your system has g++ installed: yes (version 9.4).
    Checking if your kernel supports __sync_* builtin functions: yes.
    Location of tcl.h: /usr/include/tcl8.6
    Location of tk.h: /usr/include/tcl8.6
    Location of Tcl 8.6 library: /usr/lib/x86_64-linux-gnu
    Location of Tk 8.6 library: /usr/lib/x86_64-linux-gnu
    Location of X11/Xlib.h: /usr/include
    Location of X11 library: /usr/lib/x86_64-linux-gnu
    Location of Xcursor library: /usr/lib/x86_64-linux-gnu
    Location of fontconfig library: /usr/lib/x86_64-linux-gnu
    Checking your fontconfig version: 2.13
    Checking if your system has X11/SM/SM.h: yes.
    Checking if your system has fontconfig: yes.
    Checking if your system has freetype2: yes.
    Checking if your kernel has inotify support: yes
    Checking if your system already has zlib installed: yes.
    Checking if your system already has zziplib installed: yes.
    Checking if your system already has expat installed: yes.
    Checking if your system already has gdbm installed: yes.


IMPORTANT NOTE:
-------------------------------------------------------------------------------
On this insane system debugging of own processes is not allowed due to the
kernel hardening paranoia. You might change this behaviour, see
<http://sourceforge.net/p/scidb/mailman/message/28418675/>, and then configure
again, otherwise you will not see useful error messages in case of internal
errors.
Makefile.in configured for your system was written.
Now just type "make" to compile Scidb.
```


And make:


```
make
make[1]: 'scidb-beta.1.gz' está atualizado.
Compiling db_consumer.cpp                 [-Wall -g -I/usr/include/tcl8.6 -DSCI_NAMEBASE_FIX=1]
In file included from ../mstl/m_bitset.h:266,
                 from db_annotation.h:34,
                 from db_consumer.cpp:29:
../mstl/m_bitset.ipp: In member function ‘void mstl::bitset::fill(mstl::bitset::size_type, mstl::bitset::size_type, unsigned char)’:
../mstl/m_bitset.ipp:385:66: warning: ‘void* memset(void*, int, size_t)’ writing to an object of non-trivial type ‘mstl::bitset::bitfield’ {aka ‘class mstl::bitfield<long unsigned int>’}; use assignment instead [-Wclass-memaccess]
  385 |  ::memset(m_bits + first, value, sizeof(m_bits[0])*(last - first));
  In file included from db_common.h:32,
                 from db_provider.h:30,
                 from db_consumer.h:30,
                 from db_consumer.cpp:27:
../mstl/m_bitfield.h:25:7: note: ‘mstl::bitset::bitfield’ {aka ‘class mstl::bitfield<long unsigned int>’} declared here
   25 | class bitfield
      |       ^~~~~~~~
In file included from ../mstl/m_memblock.h:71,
                 from ../mstl/m_vector.h:24,
                 from db_move_info_set.h:34,
                 from db_consumer.h:34,
                 from db_consumer.cpp:27:
../mstl/m_memblock.ipp: In instantiation of ‘mstl::memblock<U>& mstl::memblock<T>::operator=(mstl::memblock<T>&&) [with T = db::Mark]’:
../mstl/m_vector.ipp:790:35:   required from ‘mstl::vector<T>& mstl::vector<T>::operator=(mstl::vector<T>&&) [with T = db::Mark]’
db_mark_set.ipp:124:34:   required from here
../mstl/m_memblock.ipp:134:22: error: no matching function for call to ‘mstl::memblock<db::Mark>::~memblock()’
  134 |   memblock::~memblock();
      |   ~~~~~~~~~~~~~~~~~~~^~
../mstl/m_memblock.ipp:45:1: note: candidate: ‘mstl::memblock<T>::~memblock() [with T = db::Mark]’
   45 | memblock<T>::~memblock() throw()
      | ^~~~~~~~~~~
../mstl/m_memblock.ipp:45:1: note:   candidate expects 1 argument, 0 provided
In file included from ../mstl/m_vector.h:189,
                 from db_move_info_set.h:34,
                 from db_consumer.h:34,
                 from db_consumer.cpp:27:
../mstl/m_vector.ipp: In instantiation of ‘void mstl::vector<T>::insert_aux(mstl::vector<T>::iterator, mstl::vector<T>::const_reference) [with T = mstl::pair<mstl::string, unsigned int>; mstl::vector<T>::iterator = mstl::pointer_iterator<mstl::pair<mstl::string, unsigned int> >; mstl::vector<T>::const_reference = const mstl::pair<mstl::string, unsigned int>&; mstl::vector<T>::value_type = mstl::pair<mstl::string, unsigned int>]’:
../mstl/m_vector.ipp:519:2:   required from ‘mstl::vector<T>::iterator mstl::vector<T>::insert(mstl::vector<T>::iterator, mstl::vector<T>::const_reference) [with T = mstl::pair<mstl::string, unsigned int>; mstl::vector<T>::iterator = mstl::pointer_iterator<mstl::pair<mstl::string, unsigned int> >; mstl::vector<T>::const_reference = const mstl::pair<mstl::string, unsigned int>&; mstl::vector<T>::value_type = mstl::pair<mstl::string, unsigned int>]’
../mstl/m_vector.ipp: In instantiation of ‘void mstl::vector<T>::insert_aux(mstl::vector<T>::iterator, mstl::vector<T>::const_reference) [with T = mstl::pair<mstl::string, unsigned int>; mstl::vector<T>::iterator = mstl::pointer_iterator<mstl::pair<mstl::string, unsigned int> >; mstl::vector<T>::const_reference = const mstl::pair<mstl::string, unsigned int>&; mstl::vector<T>::value_type = mstl::pair<mstl::string, unsigned int>]’:
../mstl/m_vector.ipp:519:2:   required from ‘mstl::vector<T>::iterator mstl::vector<T>::insert(mstl::vector<T>::iterator, mstl::vector<T>::const_reference) [with T = mstl::pair<mstl::string, unsigned int>; mstl::vector<T>::iterator = mstl::pointer_iterator<mstl::pair<mstl::string, unsigned int> >; mstl::vector<T>::const_reference = const mstl::pair<mstl::string, unsigned int>&; mstl::vector<T>::value_type = mstl::pair<mstl::string, unsigned int>]’
../mstl/m_map.ipp:233:5:   required from ‘mstl::map<K, V>::mapped_type& mstl::map<K, V>::operator[](mstl::map<K, V>::const_key_ref) [with K = mstl::string; V = unsigned int; mstl::map<K, V>::mapped_type = unsigned int; mstl::map<K, V>::const_key_ref = const mstl::string&]’
db_consumer.cpp:147:24:   required from here
../mstl/m_vector.ipp:699:13: warning: ‘void* memmove(void*, const void*, size_t)’ writing to an object of type ‘mstl::pointer_iterator<mstl::pair<mstl::string, unsigned int> >::value_type’ {aka ‘class mstl::pair<mstl::string, unsigned int>’} with no trivial copy-assignment; use copy-assignment or copy-initialization instead [-Wclass-memaccess]
699 |    ::memmove( pointer(position) + 1,
      |    ~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~
  700 |        pointer(position),
      |        ~~~~~~~~~~~~~~~~~~
  701 |        mstl::distance(position, end())*sizeof(value_type));
      |        ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In file included from ../mstl/m_map.h:23,
                 from db_engine_list.h:28,
                 from db_consumer.h:35,
                 from db_consumer.cpp:27:
../mstl/m_pair.h:25:7: note: ‘mstl::pointer_iterator<mstl::pair<mstl::string, unsigned int> >::value_type’ {aka ‘class mstl::pair<mstl::string, unsigned int>’} declared here
25 | class pair
      |       ^~~~
In file included from ../mstl/m_uninitialized.h:56,
                 from ../mstl/m_vector.ipp:19,
                 from ../mstl/m_vector.h:189,
                 from db_move_info_set.h:34,
                 from db_consumer.h:34,
                 from db_consumer.cpp:27:
../mstl/m_uninitialized.ipp: In instantiation of ‘static T* mstl::bits::uninitialized_pod<NBytes>::copy(InputIterator, InputIterator, T*) [with InputIterator = mstl::pair<mstl::string, unsigned int>*; T = mstl::pair<mstl::string, unsigned int>; long unsigned int NBytes = 32]’:
../mstl/m_uninitialized.ipp:95:44:   required from ‘static T* mstl::bits::uninitialized<1>::copy(InputIterator, InputIterator, T*) [with InputIterator = mstl::pair<mstl::string, unsigned int>*; T = mstl::pair<mstl::string, unsigned int>]’
../mstl/m_uninitialized.ipp:158:56:   required from ‘T* mstl::uninitialized_move(T*, T*, T*) [with T = mstl::pair<mstl::string, unsigned int>]’
../mstl/m_vector.ipp:409:43:   required from ‘void mstl::vector<T>::reserve(mstl::vector<T>::size_type) [with T = mstl::pair<mstl::string, unsigned int>; mstl::vector<T>::size_type = long unsigned int]’
../mstl/m_map.ipp:32:80:   required from ‘void mstl::map<K, V>::reserve(mstl::map<K, V>::size_type) [with K = mstl::string; V = unsigned int; mstl::map<K, V>::size_type = long unsigned int]’
db_engine_list.ipp:36:69:   required from here
../mstl/m_uninitialized.ipp:60:12: warning: ‘void* memmove(void*, const void*, size_t)’ writing to an object of type ‘class mstl::pair<mstl::string, unsigned int>’ with no trivial copy-assignment; use copy-assignment or copy-initialization instead [-Wclass-memaccess]
   60 |   ::memmove(result, first, NBytes*(last - first));
      |   ~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In file included from ../mstl/m_map.h:23,
                 from db_engine_list.h:28,
                 from db_consumer.h:35,
                 from db_consumer.cpp:27:
../mstl/m_pair.h:25:7: note: ‘class mstl::pair<mstl::string, unsigned int>’ declared here
   25 | class pair
      |       ^~~~
In file included from ../mstl/m_uninitialized.h:56,
                 from ../mstl/m_vector.ipp:19,
                 from ../mstl/m_vector.h:189,
                 from db_move_info_set.h:34,
                 from db_consumer.h:34,
                 from db_consumer.cpp:27:
                 ../mstl/m_uninitialized.ipp: In instantiation of ‘static T* mstl::bits::uninitialized_pod<NBytes>::copy(InputIterator, InputIterator, T*) [with InputIterator = mstl::string*; T = mstl::string; long unsigned int NBytes = 24]’:
../mstl/m_uninitialized.ipp:95:44:   required from ‘static T* mstl::bits::uninitialized<1>::copy(InputIterator, InputIterator, T*) [with InputIterator = mstl::string*; T = mstl::string]’
../mstl/m_uninitialized.ipp:158:56:   required from ‘T* mstl::uninitialized_move(T*, T*, T*) [with T = mstl::string]’
../mstl/m_vector.ipp:409:43:   required from ‘void mstl::vector<T>::reserve(mstl::vector<T>::size_type) [with T = mstl::string; mstl::vector<T>::size_type = long unsigned int]’
../mstl/m_vector.ipp:310:3:   required from ‘mstl::vector<T>& mstl::vector<T>::operator=(const mstl::vector<T>&) [with T = mstl::string]’
db_consumer.cpp:83:24:   required from here
../mstl/m_uninitialized.ipp:60:12: warning: ‘void* memmove(void*, const void*, size_t)’ writing to an object of type ‘class mstl::string’ with no trivial copy-assignment; use copy-assignment or copy-initialization instead [-Wclass-memaccess]
   60 |   ::memmove(result, first, NBytes*(last - first));
      |   ~~~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In file included from db_move.h:38,
                 from db_move_list.h:30,
                 from db_board.h:34,
                 from db_consumer.h:31,
                 from db_consumer.cpp:27:
../mstl/m_string.h:28:7: note: ‘class mstl::string’ declared here
   28 | class string
      |       ^~~~~~
make[2]: *** [Makefile:162: db_consumer.o] Erro 1
make[1]: *** [Makefile:205: recursive] Erro 1
make: *** [Makefile:20: all] Erro 2
```


Can you help me solving out these errors please?


Thanks a lot in advance!


Gabriel Queiroz

---

### Post by coffeecat on 2022-11-05
Post moved to its own thread from this thread: [https://ubuntuforums.org/showthread.php?t=2472649](https://ubuntuforums.org/showthread.php?t=2472649)

@gabaozin, please start your own threads. You can always link back to another thread if you think it relevant. The thread you posted to was old and marked solved, which makes it unlikely that you would have got help there. Since you are running Zorin, not Ubuntu, I have moved your post to the appropriate sub-forum.

---

### Post by cmcanulty on 2022-11-05
I am hammered today but will get back to you tomorrow. First though did you try my tutorial? I will paste it below. So far it works on every Ubuntu except one stopped working a month or so ago unfortunately it is my main machine and loads the scidb splash screen and then crashes. But I run numerous machines for our library and all but that one it works fine.

```
Scidb chess install tutorial for Ubuntu, Mint, Debian

Since the recent kernel updates scidb chess has numerous errors when trying to install. I have worked on this for a few weeks and tested it on several Ubuntu 20.04 and 22.04 computers and it works well. This looks involved but is quite easy to do step by step.

Go to
https://sourceforge.net/p/scidb/code/HEAD/tree/  and click on download snapshot r1531

I downloaded the file to my home folder to make things simple.

Extract the file

In the extracted directory named scidb-code-r1531-trunk   open the INSTALL file and install the several required dependencies. After number 6 stop. Note on one system number 2: sudo apt-get install libfreetype6-dev wasn't available but this didn't cause any issues

Now edit a file in your scidb-code-r1531-trunk directory: go to line 30 in:

  /scidb-code-r1531-trunk/src/sys/sys_info.cpp

you are going to remove the # from the beginning of the line to // so change line 30 as follows:

 change it from:    # include <sys/sysctl.h>

to

      // # include <sys/sysctl.h>

save and close that file

Then scidb wants an older version of gcc than Ubuntu uses so follow these steps one at a time. (The newest version scidb accepts is 9)

sudo apt update && sudo apt upgrade -y

sudo apt install build-essential -y

sudo apt install gcc-9 g++-9

sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 40 --slave /usr/bin/g++ g++ /usr/bin/g++-9 --slave /usr/bin/gcov gcov /usr/bin/gcov-9

gcc --version

Next install  tcl-dev  & tk & tk-dev  using whatever are the current versions

Now open a terminal in your scidb-code-r1531-trunk directory and enter these commands one at a time. They run for a while. Don't include the quotes.

type "./configure"

then “make clean”  (this just grabs anything you missed and kicks out an error there are any)

then  "make"

then "make clean"

then "sudo make install"

Once it successfully installs you can access scidb with it's blue icon and a black knight from your applications menu or by typing scidb in a terminal. A very special thanks to computersavvy a Senior Member of the LinuxQuestions  Linux Software forum who was quite patient helping me through the fix for the  sys_info.cpp file which had me stalled and quite frustrated for a long while.
https://www.linuxquestions.org/questions/linux-software-2/issue-with-install-of-app-4175712064/


Please contact me if you have any corrections, updates, suggestions, or comments. It is a wonderful program and well worth the effort to install. It is the only way to read chessbase files in a native linux app. Also it reads pgn files and has a ton of great features and a very beautiful interface.

Carol McAnulty


```

---

### Post by &amp;KyT$0P# on 2022-11-06
> **cmcanulty said:**
> sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-9 40 --slave /usr/bin/g++ g++ /usr/bin/g++-9 --slave /usr/bin/gcov gcov /usr/bin/gcov-9

Although gcc-9 is likely already default on this OP's 20.04-based system, this suggestion is still unwise.  If gcc <= 9.x is not already default, use the [non-invasive way to have scidb compile with gcc-9]("https://ubuntuforums.org/showthread.php?t=2477924&p=14109851&viewfull=1#post14109851").

---

### Post by cmcanulty on 2022-11-06
I am afraid I need more instruction on how to do as you say on the non invasive way of compiling scidb with gcc. I did the help command and got a bunch of options but not sure what to do with it, thank you


```
cmcanulty@Dell660s:~/scidb-code-r1531-trunk$ ./configure --help
Usage: ./configure [OPTION]... [VAR=VALUE]...

To assign environment variables (e.g., CC, CFLAGS...), specify them as
VAR=VALUE.  See below for descriptions of some of the useful variables.

Defaults for the options are specified in brackets.

Configuration:
  -h, --help                display this help and exit
  -n, --no-create           do not create output files

Installation directories:
  --prefix=PREFIX           install architecture-independent files in PREFIX
                            [/usr/local]
  --exec-prefix=EPREFIX     install architecture-dependent files in EPREFIX
                            [/usr/local]

By default, `make install' will install all the files in
`/usr/local/bin', `/usr/local/lib' etc.  You can specify
an installation prefix other than `/usr/local' using `--prefix',
for instance `--prefix=/home/cmcanulty'.

For better control, use the options below.

Fine tuning of the installation directories:
  --bindir=DIR               user executables [EPREFIX/bin]
  --enginesdir=DIR           engines (executables) [EPREFIX/games]
  --datadir=DIR              read-only architecture-independent data [PREFIX/share]
  --libdir=DIR               object code libraries [EPREFIX/lib]
  --mandir=DIR               man documentation [PREFIX/man]
  --fontdir=DIR              truetype fonts [PREFIX/share/fonts]

Fine tuning of the installation directory (see INSTALL):
  --destdir=DIR              installation directory for packaging

Program names:
  --program-suffix=SUFFIX    append SUFFIX to installed program names

Tcl/Tk features:
  --tcl-version=VER          Tcl/Tk version [8.6]
  --tcl-includes=DIR         Tcl include files are in DIR
  --tcl-libraries=DIR        Tcl library files are in DIR
  --tk-includes=DIR          Tk include files are in DIR
  --tk-libraries=DIR         Tk library files are in DIR

X features:
  --x-includes=DIR           X include files are in DIR
  --x-libraries=DIR          X library files are in DIR
  --xcursor-libraries=DIR    Xcursor library files are in DIR
  --fontconfig-libraries=DIR fontconfig library files are in DIR

GNU compiler features:
  --gcc-version=VER          GNU compiler version
                             you may use 'clang' instead for the clang compiler

Packages:
  --with-zlib-inc=DIR        path to Zlib compression library headers
  --with-zlib-lib=DIR        link options for Zlib compression library
  --with-zziplib-inc=DIR     path to Zziplib zip library headers
  --with-zziplib-lib=DIR     link options for Zziplib zip library
  --with-expat-inc=DIR       path to Expat XML Parser headers
  --with-expat-lib=DIR       link options for Expat XML Parser library

  --force-bundled-zlib       [default=no]
  --force-bundled-zziplib    [default=no]
  --force-bundled-expat      [default=no]
  --force-bundled-gdbm       [default=no]

Optional Features:
  --disable-FEATURE          do not include FEATURE (same as --enable-FEATURE=no)
  --enable-FEATURE[=ARG]     include FEATURE [ARG=yes]
  --enable-freedesktop       install freedesktop.org files (mime types and desktop
                             file) [default=yes]
  --enable-fam               build with FAM support [default=no]
  --enable-symbols           build with debugging symbols [default=yes]
  --enable-assertions        build with assertions (slows down the program)
                             [default=yes]
  --enable-sse2              enable sse2 support (fast JPEG decompression)
                             [default=no]
  --enable-gprof-profiling   enable gprof profiling (slows down the program)
                             [default=no]
  --enable-gcov-coverage     enable coverage (slows down the program)
                             [default=no]
  --enable-inline-text      enable inline text widget (revised implementation) [default=yes]

Additional Options:
  --suppress-insane-message  suppress the message about an insane distribution
                             (not recommended)

Some influential environment variables:
  AR           AR for the host [ar]
  ARFLAGS      Flags for AR [rc]
  CC           C compiler command [gcc]
  CFLAGS       C compiler flags [-Wall]
  CXX          C++ compiler command [g++]
  CXXFLAGS     C++ compiler flags [-Wall]
  LDFLAGS      linker flags, e.g. -L<lib dir> if you have libraries in a
               nonstandard directory <lib dir>
  OPTIMIZE     C/C++ optimization flags []
  RANLIB       RANLIB for the host [ranlib]
  STRIP        STRIP for the host [strip]
  SYS_CFLAGS   system specific C compiler flags
  SYS_CXXFLAGS system specific C++ compiler flags
  SYS_LDFLAGS  system specific linker flags

Use these variables to override the choices made by `configure' or to help
it to find libraries and programs with nonstandard names/locations.
cmcanulty@Dell660s:~/scidb-code-r1531-trunk$ 

```

---

### Post by &amp;KyT$0P# on 2022-11-06
Just run
```
export CC=gcc-9 CXX=g++-9
```
before running [FONT=Courier New]./configure[/FONT]

---

### Post by cmcanulty on 2022-11-06
just to be clear I run that command in a terminal but not from within the scidb directory?

---

### Post by &amp;KyT$0P# on 2022-11-06
> **cmcanulty said:**
> just to be clear I run that command in a terminal but not from within the scidb directory?

You can run it from any directory.  It only has to be run in the same Terminal window where you will run [FONT=Courier New]./configure[/FONT]

---

### Post by cmcanulty on 2022-11-06
Thanks I still can't get scidb to not crash after the splash screen on my main computer, it works ine in all the other machines . It gives these errors. The ./configure runs fine but the make gives errors. Thank you

```
cmcanulty@Dell660s:~/scidb-code-r1531-trunk$ make
make[1]: 'scidb.1.gz' is up to date.
Compiling cql/cql_common.cpp              [-DSCI_NAMEBASE_FIX=1]
In file included from ../mstl/m_bitfield.ipp:19,
                 from ../mstl/m_bitfield.h:199,
                 from ./db_common.h:32,
                 from cql/cql_common.h:30,
                 from cql/cql_common.cpp:27:
./db_common.ipp: In function ‘unsigned int db::result::value(db::result::ID)’:
./db_common.ipp:315:28: error: ‘U_NUMBER_OF’ was not declared in this scope
  315 |  M_ASSERT(size_t(result) < U_NUMBER_OF(Value));
      |                            ^~~~~~~~~~~
../mstl/m_assert.h:45:53: note: in definition of macro ‘M_CHECK’
   45 | #define M_CHECK(Exc,expr) ({ if (__builtin_expect(!(expr), 0)) M_THROW(Exc(#expr)); })
      |                                                     ^~~~
./db_common.ipp:315:2: note: in expansion of macro ‘M_ASSERT’
  315 |  M_ASSERT(size_t(result) < U_NUMBER_OF(Value));
      |  ^~~~~~~~
cql/cql_common.cpp: In function ‘db::country::Code cql::country::lookupIso3166_2(const mstl::string&)’:
cql/cql_common.cpp:315:11: error: ‘U_NUMBER_OF’ was not declared in this scope
  315 |           U_NUMBER_OF(Table),
      |           ^~~~~~~~~~~
make[2]: *** [Makefile:162: cql/cql_common.o] Error 1
make[1]: *** [Makefile:205: recursive] Error 1
make: *** [Makefile:20: all] Error 2
cmcanulty@Dell660s:~/scidb-code-r1531-trunk$ 

```

---

### Post by &amp;KyT$0P# on 2022-11-06
It still compiles and runs fine for me on up-to-date Xubuntu 22.04 with the only change to source code being this -
```
diff --git a/src/sys/sys_info.cpp b/src/sys/sys_info.cpp
index 29f3238..3808b0a 100644
--- a/src/sys/sys_info.cpp
+++ b/src/sys/sys_info.cpp
@@ -27,7 +27,7 @@
 # include <stdlib.h>
 # include <unistd.h>
 # include <sys/types.h>
-# include <sys/sysctl.h>
+# include <linux/sysctl.h>
 
 #ifdef __hpux
 # include <sys/pstat.h>

```
(Although all I'm testing is playing chess moves in the Board tab.)

I would suggest uninstalling scidb from the affected system and starting over with a fresh unzipping of the source code .zip, making only this one line code change and try compiling from scratch from there.

---

### Post by cmcanulty on 2022-11-06
sorry to be so dumb but where do I run that code or what file do I alter?

---

### Post by &amp;KyT$0P# on 2022-11-06
> **cmcanulty said:**
> sorry to be so dumb but where do I run that code or what file do I alter?

It's a [git style diff]("https://therobinkim.com/blog/how-to-read-a-git-diff/") comparing the original scidb source tree to the change I made.

---

### Post by cmcanulty on 2022-11-06
god I feel so stupid I don't know which file to change and what change to do

---

### Post by cmcanulty on 2022-11-06
OK I think I got it I had already commented out the 
# include <sys/sysctl.h>
and now I added 
# include <linux/sysctl.h>
but no change it still gets the same errors on make command

---

### Post by &amp;KyT$0P# on 2022-11-06
> **cmcanulty said:**
> OK I think I got it I had already commented out the 
# include <sys/sysctl.h>
and now I added 
# include <linux/sysctl.h>

Yes exactly :KS

> no change it still gets the same errors on make command

The thing it thinks is not declared is supposed to be defined in the scidb source tree, in [FONT=Courier New]src/util/u_base.h[/FONT]

My best guess would be that the scidb source tree you're compiling from is corrupted somehow, in which case a completely fresh copy of the source code should fix that.

---

### Post by cmcanulty on 2022-11-06
I've done that several times with no luck

---

