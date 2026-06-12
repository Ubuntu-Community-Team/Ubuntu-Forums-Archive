---
title: "Howto: Install Boost from source"
date: 2009-06-07
forum: Tutorials
---

### Post by kayvortex on 2009-06-07
Welcome. This a guide on how to install the [Boost libraries]("http://www.boost.org") from source. Although the boost libraries are available in the universe repository there are people who have tried to install from source for one reason or another (myself included) and, because of the unfamiliar method by which Boost choose to create their libraries, fall into trouble or else never really understand what to do (even though it's not all that hard actually).
This is only a very simple guide on how to get the source compiled and installed and I wont go into more advanced topics on how to customize the installation (because I don't know myself) or on how to cross-compile (since I've tried and given up on that -- the problem being that the boost build system doesn't use the correct cross-compiling binaries for compiling and creating the libraries and it's next to Alchemy trying to understand how to get the thing to use the correct ones. As a last resort, not even creating symlinks from the the cross-compiling binary to the corresponding normal build binary didn't work!).

[SIZE="4"]**-1) General Information**[/SIZE]

This guide is specifically written for boost libraries version 1.39.0. The general idea of what we're doing will *probably* still apply for some of the more recent older library version; but, there will be **crucial** differences, like the fact that the file *configure* will exist instead of *bootstrap.sh*.

[SIZE="4"]**0) Pre-requisites**[/SIZE]

[SIZE="3"]0.1)[/SIZE]
You will need the necessary compiling tools (g++, ld, etc...); so, first, install them:
```
sudo aptitude install build-essential g++
```

[SIZE="3"]0.2)[/SIZE]
You will need the source code! Boost's website is not the best when it comes to finding where things are, so just navigate to their [getting started]("http://www.boost.org/doc/libs/1_39_0/more/getting_started/unix-variants.html") page and under the section *Get Boost* follow the link to the download page and download tar.bz2 file (the tar.7z file has Windows line-terminators, so reading those files in Linux will cause errors). Incidentally, that *getting started* page is the general reference from which I've derived this guide (along with a bit of trial and much error).

[SIZE="4"]**1) Compile the library**[/SIZE]

[SIZE="3"]1.1)[/SIZE]
Go to where you downloaded the directory and uncompress it:
```
cd *download_location*
tar xjf boost_1_39_0.tar.bz2
```
Note that the uncompressed source is over 250Mb; so if space is an issue, make the necessary sacrifices!
Then change directory into the boost directory:
```
cd ./boost_1_39_0
```

[SIZE="3"]1.2)[/SIZE]
Next, we'll need to build the bjam binary and perhaps also set some options on what to compile and where to. **Read the next three sub-sections carefully and read it all before you do anything!** 

[SIZE="3"]1.2.1)[/SIZE]
Firstly, you will not want to compile the *whole* boost library since that means compiling a lot of libraries that you don't want or wont use. So, to see a list of the libraries that need compiling, run:
```
./bootstrap.sh --show-libraries
``` 
Pick which ones you want and remember them: I'll be choosing *filesystem*, *program_options* and *system*. Note that picking *system* is **needed** since it contains the error class that *filesystem* uses, and I bet that, since the majority of you readers will be looking to compile the filesystem library, this means cutting a few problems out later on for a lot of you!
What you'll need to run is the command:
```
./bootstrap.sh --with-library=filesytem,program_options,system
```
**But don't do that just yet: keep reading!**
If you *do* want to compile the whole damned thing, then you don't need to bother with the command above: you'll just run bootstrap.sh as it is:
```
./bootstrap.sh
```
**Again, don't run anything yet: still keep on reading!**

[SIZE="3"]1.2.2)[/SIZE]
Next, you'll need to consider where you want the library installed to. By default, the header files are installed to /usr/local/include, and the libraries themselves are installed to /usr/local/lib. These locations will be more than adequate (it's not recommended to install stuff to /usr/include, /usr/include/lib or /lib); but, if you do want/need to specify a different location, you'll need to run bootstrap.sh like this:
```
./bootstrap --libdir=*/my/lib/dir* --includedir=*/my/include/dir*
```
which will install the libraries to */my/lib/dir* and the header files to */my/include/dir*.
**Note: there is a bug in that the libraries are installed to /lib and not /usr/local/lib by default; so I'd recommend explicitly telling the build process to install to /usr/local/lib. Do this by adding the flag: --exec-prefix=/usr/local**.
**Still, don't run anything yet! Keep reading!**

[SIZE="3"]1.2.3)[/SIZE]
OK, now bring the info from the last two sub-sections together: you'll want the command:
```
./bootstrap.sh --exec-prefix=/usr/local --with-libraries=*desired_list_of_libs* --libdir=*/my/lib/dir* --includedir=*/my/include/dir*
```

For example, I want to only install the *filesystem*, *program_options*, and *system* libraries, and just to the default lib and include directories; so, I'll personally run:
```
./bootstrap.sh --with-libraries=filesystem,program_options,system --exec-prefix=/usr/local
```
Having done this (or something similar depending on what you want to do) you'll see the message:
> Bootstrapping is done. To build, run:

    ./bjam
    
To adjust configuration, edit 'project-config.jam'.
Further information:

   - Command line help:
     ./bjam --help
     
   - Getting started guide: 
     [http://www.boost.org/more/getting_started/unix-variants.html](http://www.boost.org/more/getting_started/unix-variants.html)
     
   - Boost.Build documentation:
     [http://www.boost.org/boost-build2/doc/html/index.html](http://www.boost.org/boost-build2/doc/html/index.html)

At this point, you can then do the compiling proper...

[SIZE="3"]1.2.4)[/SIZE]
Run the command:
```
./bjam
```
And that's it!

[SIZE="4"]**2) Installation**[/SIZE]

Immediately after compiling, and before we install them, the header files will be in the directory *boost*, and the libraries in the directory *stage/lib*. To install them, just run:
```
sudo ./bjam install
```
Note that, on my system, that command seems to hang for a while; so, give it a chance before killing it.

Now, there is one "bug" in the installation process. The installation procedure does not create a symlink called *libboost_filesystem.so*. It's not really a problem, but it's very useful if it does exist. Look in your library directory to see if it's there, or else create it:
```
sudo ln -s /usr/local/lib/libboost_filesystem-gcc43-mt.so /usr/local/lib/libboost_filesystem.so
```
And change */usr/local/lib* **if** you changed where you installed your libraries to at stage *1.2.3*, and amend *libboost_filesystem-gcc43-mt.so* if it's different on your system. (Post a comment if you are having trouble with this since the names will probably be different from system-to-system and **don't do anything if you're not at all sure on how libraries are named and symlinked**).

[SIZE="4"]**3) Using the libraries**[/SIZE]

This bit normally causes a few problems, so read it carefully!

[SIZE="3"]3.1)[/SIZE]
Include your header files as usual in your code like:
> #include <boost/filesystem.hpp>
and then tell your compiler where the include libraries are with a *-I* flag:
```
g++ -I/usr/local/include/boost-1_39 ...
```
**If** you changed your include directory at stage *1.2.3* by issuing:
> ./bootstrap.sh --includedir=*/my/include/dir*
then you'll need to amend the g++ command to:
```
g++ -I/my/include/dir/boost-1_39
```

[SIZE="3"]3.2)[/SIZE]
Then, we'll also need to make sure we can link to the libraries.
**If** you did not change the directory to where the libraries are installed to from the default at stage *1.2.3*, then simply run:
```
sudo ldconfig
```
And you can start linking the library as usual:
```
g++ -lboost_filesystem ...
```
**If** you did change the lib directory at stage *1.2.3* by running:
> ./bootstrap.sh --libdir=/my/lib/dir
then you'll need to run the linking stage as:
```
g++ -L/my/lib/dir -lboost_filesystem
```

Hopefully, that's it! You should now be able to use boost!


[SIZE="4"]**Problems and Updates**[/SIZE]

Leave a comment if you have a problem and I'll try to help. But, please, nothing on cross-compiling since I'll go bald trying to figure that one out! Suggestions and experiences on trying to get it to work, however, are welcome.

Also, improvements and updates to the guide are more than welcome.

---

### Post by Nikar on 2009-07-15
Hi I have followed your guide as much as I could but when I try to compile I still get some errors about boost not being found.

```
|38|error: boost/filesystem.hpp: No such file or directory|
|39|error: boost/regex.hpp: No such file or directory|
|41|error: ‘boost’ has not been declared|
|41|error: ‘filesystem’ is not a namespace-name|

```


The problems I have are in step 2, because it seems is installing the libs in /lib not in /usr/lib

I am using Code::Block as IDE but it also does not compile with make.

Very nice guide btw.
I also dont know why neither 1.38 nor 1.39 boost versions are in the repos :(

---

### Post by kayvortex on 2009-07-29
Sorry for the late-ish reply.

I tend to avoid IDE's (too bloated), so from the output you posted, it looks like it simply can't find the header files. This could be a problem with Code::Blocks, or with the installation.

So, look to see if you can compile *anything* successfully with boost included: just create a very simple file "test.cpp":
> 
#include <boost/filesystem.hpp>
int main(void) { return 0; }


Now, depending on where your boost include files are (they should be in /usr/local/include/boost-1_39), just run:
```
g++ -E -I/usr/local/include/boost-1_39 test.cpp >/dev/null
```

If that last command appears to do nothing and returns successfully, there's no problem in the installation of your header files. In that case, your problem is probably that you haven't told Code::Blocks to include the directory /usr/local/include/boost-1_39 in its include path: you'll have to look for manuals/tutorials on how to modify the IDE's include path.

Let me know what happens when you issue that command, and I'll continue (I should be able to reply on the same day at the least!)...

---

### Post by man4ish on 2009-09-08
Hi, 
I am working on shared memory . I need to use boost interprocess library. I am using eclipse ide and i have installed the boost on linux as explained in the tutorials. Libraries are in /usr/local/include/boost-1_39 and name of library is boost. But when i compile the sample program it gives the following errors.

g++ -L/usr/local/include/boost-1_39 -o"Gcount"  ./ccount.o   -lboost
/usr/bin/ld: cannot find -lboost

If i compile the same program on terminal still pblm is there. 


> **kayvortex said:**
> Sorry for the late-ish reply.

I tend to avoid IDE's (too bloated), so from the output you posted, it looks like it simply can't find the header files. This could be a problem with Code::Blocks, or with the installation.

So, look to see if you can compile *anything* successfully with boost included: just create a very simple file "test.cpp":


Now, depending on where your boost include files are (they should be in /usr/local/include/boost-1_39), just run:
```
g++ -E -I/usr/local/include/boost-1_39 test.cpp >/dev/null
```If that last command appears to do nothing and returns successfully, there's no problem in the installation of your header files. In that case, your problem is probably that you haven't told Code::Blocks to include the directory /usr/local/include/boost-1_39 in its include path: you'll have to look for manuals/tutorials on how to modify the IDE's include path.

Let me know what happens when you issue that command, and I'll continue (I should be able to reply on the same day at the least!)...

---

### Post by kayvortex on 2009-09-20
> Hi,
I am working on shared memory . I need to use boost interprocess library. I am using eclipse ide and i have installed the boost on linux as explained in the tutorials. Libraries are in /usr/local/include/boost-1_39 and name of library is boost. But when i compile the sample program it gives the following errors.

g++ -L/usr/local/include/boost-1_39 -o"Gcount" ./ccount.o -lboost
/usr/bin/ld: cannot find -lboost

If i compile the same program on terminal still pblm is there.


You're telling g++ to find the library "libboost.so" when you type the flag "-lboost". The library wont be called "boost", but probably something like "libboost_interprocess.so"; so you want something like:
```
g++ -L/usr/local/include/boost-1_39 -o"Gcount" ./ccount.o -lboost_interprocess
```

Check to see what the library is *actually* called, though, since I'm only making an educated guess.

---

### Post by man4ish on 2009-09-30
I am installing the boost on itanium (64 bit red hat) machine. I am following the three steps.
./bootstrap.sh --prefix=/usr/local
./bjam
./bjam install

After installation, libboost files are all located in
/usr/lib. 

But i am trying to run one simple code.

#include <boost/interprocess/managed_shared_memory.hpp>
#include <boost/interprocess/allocators/allocator.hpp>
#include <boost/interprocess/containers/map.hpp>
#include <boost/interprocess/containers/string.hpp>
#include <iostream>

using namespace boost::interprocess;

//Typedefs of allocators and containers
typedef managed_shared_memory::segment_manager segment_manager_t;
typedef allocator<void, segment_manager_t> void_allocator;
typedef allocator<char, segment_manager_t> char_allocator;
typedef basic_string<char, std::char_traits<char>, char_allocator> char_string;

//Definition of the map holding a string as key and complex_data as mapped type
typedef std::pair<const char_string, int> map_value_type;
typedef allocator<map_value_type, segment_manager_t>  map_value_type_allocator;
typedef map< char_string, int, std::less<char_string>, map_value_type_allocator>  complex_map_type;

int main ()
{
   shared_memory_object::remove("MySharedMemory");

   //Create shared memory
   managed_shared_memory segment(create_only,"MySharedMemory", 65536);

   //An allocator convertible to any allocator<T, segment_manager_t> type
   void_allocator alloc_inst (segment.get_segment_manager());

   //Construct the shared memory map and fill it
   complex_map_type *mymap = segment.construct<complex_map_type>("MyMap")(std::less<char_string>(), alloc_inst);
   char_string cs("test", alloc_inst);
 
   for(int i = 0; i < 100; ++i)
   {
       mymap->insert(std::pair<char_string, int>(cs , i));
   }
   return 0;
} 


 with command 
g++ program_name.cpp -lrt 

It is showing error "No such file and directory" for every header file. This code is working fine on 32 bit (installed by other person).May i know what is the pblm?

---

### Post by man4ish on 2009-09-30
I have tried to run the command as suggested by u for checking installation on linux itanium server 64 bit but i am getting the following error. May i know what is the cause of this pblm.

g++ -E -I/usr/local/include/boost-1_39 boostindex.cpp >/dev/null
In file included from /usr/local/include/boost-1_39/boost/interprocess/sync/interprocess_mutex.hpp:47,
                 from /usr/local/include/boost-1_39/boost/interprocess/mem_algo/rbtree_best_fit.hpp:27,
                 from /usr/local/include/boost-1_39/boost/interprocess/detail/managed_memory_impl.hpp:22,
                 from /usr/local/include/boost-1_39/boost/interprocess/managed_shared_memory.hpp:21,
                 from boostindex.cpp:1:
/usr/local/include/boost-1_39/boost/interprocess/detail/atomic.hpp:466:2: #error No atomic operations implemented for this platform, sorry!


Thanks in advance.
> **kayvortex said:**
> You're telling g++ to find the library "libboost.so" when you type the flag "-lboost". The library wont be called "boost", but probably something like "libboost_interprocess.so"; so you want something like:
```
g++ -L/usr/local/include/boost-1_39 -o"Gcount" ./ccount.o -lboost_interprocess
```Check to see what the library is *actually* called, though, since I'm only making an educated guess.

---

### Post by kayvortex on 2009-10-01
Well, the reason why you appear to be getting "no such file and directory" errors is because you need to tell the compiler to look in the "/usr/local/include/boost-1_39" directory. Just include the flag "-I/usr/local/include/boost-1_39" in your compiling.

> g++ -E -I/usr/local/include/boost-1_39 boostindex.cpp >/dev/null
In file included from /usr/local/include/boost-1_39/boost/interprocess/sync/interprocess_mutex.hpp:47,
from /usr/local/include/boost-1_39/boost/interprocess/mem_algo/rbtree_best_fit.hpp:27,
from /usr/local/include/boost-1_39/boost/interprocess/detail/managed_memory_impl.hpp:22,
from /usr/local/include/boost-1_39/boost/interprocess/managed_shared_memory.hpp:21,
from boostindex.cpp:1:
/usr/local/include/boost-1_39/boost/interprocess/detail/atomic.hpp:466:2: #error No atomic operations implemented for this platform, sorry!

From the looks of this message, there's a problem with the file "atomic.hpp" for your architecture. Are you sure that you've included all the necessary dependencies for this library? Because the installation process doesn't do this for you: you must read the boost manual and install them all manually.

Apart from that, there's not much else I can suggest since I neither know enough about the boost interprocess library nor have an IA64 machine to work with to be able to help you. You could try the boost message boards for help.

Edit: looking at the file "/usr/local/include/boost-1_39/boost/interprocess/detail/atomic.hpp" it looks like you need gcc version 4.0.1 or greater to work on an IA64 machine: which version of gcc are you using?

---

### Post by man4ish on 2009-10-01
I am using 3.4..6. Now i will try with 4.0.1 version. 

Thanks
> **kayvortex said:**
> Well, the reason why you appear to be getting "no such file and directory" errors is because you need to tell the compiler to look in the "/usr/local/include/boost-1_39" directory. Just include the flag "-I/usr/local/include/boost-1_39" in your compiling.



From the looks of this message, there's a problem with the file "atomic.hpp" for your architecture. Are you sure that you've included all the necessary dependencies for this library? Because the installation process doesn't do this for you: you must read the boost manual and install them all manually.

Apart from that, there's not much else I can suggest since I neither know enough about the boost interprocess library nor have an IA64 machine to work with to be able to help you. You could try the boost message boards for help.

Edit: looking at the file "/usr/local/include/boost-1_39/boost/interprocess/detail/atomic.hpp" it looks like you need gcc version 4.0.1 or greater to work on an IA64 machine: which version of gcc are you using?

---

### Post by kelargo on 2010-08-21
I am using Lucid and followed this tutorial to install boost 1.44.
the application needs a newer version of boost than what is in the repositories.

I didn't have a full development environment and encountered errors installing boost. So through synaptic, I installed the following to get missing headers.

libbz2-dev 
python-dev

Then did a ./bjam -a to rebuild everything. all seems ok now. 

regards

---

### Post by auiG on 2011-02-15
I followed the above script. Now the header are in /usr/local/include and the builded libraries in /usr/local/lib. I tired to compile the example in test.cpp:

```
#include <boost/thread.hpp> 
#include <iostream> 

void wait(int seconds) 
{ 
  boost::this_thread::sleep(boost::posix_time::seconds(seconds)); 
} 

void thread() 
{ 
  for (int i = 0; i < 5; ++i) 
  { 
    wait(1); 
    std::cout << i << std::endl; 
  } 
} 

int main() 
{ 
  boost::thread t(thread); 
  t.join(); 
} 
``` For compiling I use 

g++ test.cpp -otest

I get the following error messages:

```
test.cpp:(.text+0x9f): undefined reference to `boost::thread::join()'
test.cpp:(.text+0xab): undefined reference to `boost::thread::~thread()'
test.cpp:(.text+0xca): undefined reference to `boost::thread::~thread()'
/tmp/ccNPcdEE.o: In function `boost::detail::thread_data_base::thread_data_base()':
test.cpp:(.text._ZN5boost6detail16thread_data_baseC2Ev[boost::detail::thread_data_base::thread_data_base()]+0x26): undefined reference to `vtable for boost::detail::thread_data_base'
/tmp/ccNPcdEE.o: In function `void boost::this_thread::sleep<boost::posix_time::seconds>(boost::posix_time::seconds const&)':
test.cpp:(.text._ZN5boost11this_thread5sleepINS_10posix_time7secondsEEEvRKT_[void boost::this_thread::sleep<boost::posix_time::seconds>(boost::posix_time::seconds const&)]+0x35): undefined reference to `boost::this_thread::sleep(boost::posix_time::ptime const&)'
/tmp/ccNPcdEE.o: In function `boost::thread::thread<void (*)()>(void (*)(), boost::disable_if<boost::is_convertible<void (*&)(), boost::detail::thread_move_t<void (*)()> >, boost::thread::dummy*>::type)':
test.cpp:(.text._ZN5boost6threadC1IPFvvEEET_NS_10disable_ifINS_14is_convertibleIRS4_NS_6detail13thread_move_tIS4_EEEEPNS0_5dummyEE4typeE[boost::thread::thread<void (*)()>(void (*)(), boost::disable_if<boost::is_convertible<void (*&)(), boost::detail::thread_move_t<void (*)()> >, boost::thread::dummy*>::type)]+0x32): undefined reference to `boost::thread::start_thread()'
/tmp/ccNPcdEE.o: In function `boost::detail::thread_data<void (*)()>::~thread_data()':
test.cpp:(.text._ZN5boost6detail11thread_dataIPFvvEED1Ev[boost::detail::thread_data<void (*)()>::~thread_data()]+0x1f): undefined reference to `boost::detail::thread_data_base::~thread_data_base()'
/tmp/ccNPcdEE.o: In function `boost::detail::thread_data<void (*)()>::~thread_data()':
test.cpp:(.text._ZN5boost6detail11thread_dataIPFvvEED0Ev[boost::detail::thread_data<void (*)()>::~thread_data()]+0x1f): undefined reference to `boost::detail::thread_data_base::~thread_data_base()'
/tmp/ccNPcdEE.o:(.rodata._ZTIN5boost6detail11thread_dataIPFvvEEE[typeinfo for boost::detail::thread_data<void (*)()>]+0x10): undefined reference to `typeinfo for boost::detail::thread_data_base'
collect2: ld returned 1 exit status
```Does anybody know, where the mistake is?

Regards

---

### Post by aamikkelsen on 2011-03-12
I have exactly the same problem.

---

### Post by hrcariagajr on 2011-07-07
> **auiG said:**
> I followed the above script. Now the header are in /usr/local/include and the builded libraries in /usr/local/lib. I tired to compile the example in test.cpp:

...

For compiling I use 

g++ test.cpp -otest


try to compile it with:

```

g++ test.cpp -otest -I/usr/local/include -L/usr/local/lib -lboost_thread

```

---

### Post by ccervo on 2013-07-08
Have a problem based on your post I thought you might help. Was happily using Eclipse, BJAM & QT on Ubuntu for C++ development . I then used synaptic to upgrade to newest LST release of Ubuntu, (12.04). After upgrade my builds no longer work. I get error messages from BJAM complaining about jamfiles that previously worked perfectly.
 example
jamfile contains:
SHELL "mkdir -vp $(SOLUTION_ROOT)/log $(SOLUTION_ROOT)/conf" ;
bjam reports error:
/home/ccervo/LoggerWrk/cipLogger/src/Jamfile:31: in modules.load
*** argument error
* rule SHELL ( command : * )
* called with: (  )
* missing argument command
(builtin):see definition of rule 'SHELL' being called

I strongly suspect the upgrade did not properly install bjam or some associated libraries or tools. 

Can you advise on best way to uninstall or clean-up bjam and then reinstall or advise on some other method to troubleshoot.?
:(

---

