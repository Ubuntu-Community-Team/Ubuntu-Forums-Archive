---
title: "&quot;undefined reference to ...&quot; problem compiling hdf5-1.8.18 in Cygwin"
date: 2017-03-05
forum: Windows
---

### Post by kciveng on 2017-03-05
Hello All
I downloaded source files of hdf5-1.8.18 from the hdfgroup website. I try to install it on Cygwin but I face some errors that has really made me confused for several days. Of course it is most likely because I'm amateur Linux user.

I configure the files without any problem by the code
```
./configure
```

But by running the "make" command the following statements appears finally:

```


.
.
.

dynlib3.c: In function &#8216;H5PLget_plugin_info&#8217;:
dynlib3.c:45:15: warning: function might be candidate for attribute &#8216;const&#8217; [-Wsuggest-attribute=const]
 const void   *H5PLget_plugin_info(void) {return H5Z_DYNLIB3;}
               ^
  CCLD     libdynlib3.la
  CC       dynlib4.lo
dynlib4.c: In function &#8216;H5PLget_plugin_type&#8217;:
dynlib4.c:40:15: warning: function might be candidate for attribute &#8216;const&#8217; [-Wsuggest-attribute=const]
 H5PL_type_t   H5PLget_plugin_type(void) {return H5PL_TYPE_FILTER;}
               ^
dynlib4.c: In function &#8216;H5PLget_plugin_info&#8217;:
dynlib4.c:41:16: warning: function might be candidate for attribute &#8216;const&#8217; [-Wsuggest-attribute=const]
 const void    *H5PLget_plugin_info(void) {return H5Z_DYNLIB4;}
                ^
dynlib4.c: In function &#8216;H5Z_filter_dynlib4&#8217;:
dynlib4.c:89:14: warning: cannot optimize loop, the loop counter may overflow [-Wunsafe-loop-optimizations]
         while(buf_left > 0) {
              ^
dynlib4.c:96:14: warning: cannot optimize loop, the loop counter may overflow [-Wunsafe-loop-optimizations]
         while(buf_left > 0) {
              ^
  CCLD     libdynlib4.la
.libs/dynlib4.o:dynlib4.c:(.text+0x3c): undefined reference to `H5get_libversion'
.libs/dynlib4.o:dynlib4.c:(.text+0x3c): relocation truncated to fit: R_X86_64_PC32 against undefined symbol `H5get_libversion'
.libs/dynlib4.o:dynlib4.c:(.text+0x69): undefined reference to `H5open'
.libs/dynlib4.o:dynlib4.c:(.text+0x69): relocation truncated to fit: R_X86_64_PC32 against undefined symbol `H5open'
.libs/dynlib4.o:dynlib4.c:(.text+0x77): undefined reference to `H5open'
.libs/dynlib4.o:dynlib4.c:(.text+0x77): relocation truncated to fit: R_X86_64_PC32 against undefined symbol `H5open'
.libs/dynlib4.o:dynlib4.c:(.text+0x85): undefined reference to `H5open'
.libs/dynlib4.o:dynlib4.c:(.text+0x85): relocation truncated to fit: R_X86_64_PC32 against undefined symbol `H5open'
.libs/dynlib4.o:dynlib4.c:(.text+0xc1): undefined reference to `H5Epush2'
.libs/dynlib4.o:dynlib4.c:(.text+0xc1): relocation truncated to fit: R_X86_64_PC32 against undefined symbol `H5Epush2'
.libs/dynlib4.o:dynlib4.c:(.text+0xf5): undefined reference to `H5open'
.libs/dynlib4.o:dynlib4.c:(.text+0xf5): relocation truncated to fit: R_X86_64_PC32 against undefined symbol `H5open'
.libs/dynlib4.o:dynlib4.c:(.text+0x103): undefined reference to `H5open'
.libs/dynlib4.o:dynlib4.c:(.text+0x103): relocation truncated to fit: R_X86_64_PC32 against undefined symbol `H5open'
.libs/dynlib4.o:dynlib4.c:(.text+0x111): undefined reference to `H5open'
.libs/dynlib4.o:dynlib4.c:(.text+0x111): relocation truncated to fit: R_X86_64_PC32 against undefined symbol `H5open'
.libs/dynlib4.o:dynlib4.c:(.rdata$.refptr.H5E_ERR_CLS_g[.refptr.H5E_ERR_CLS_g]+0x0): undefined reference to `H5E_ERR_CLS_g'
.libs/dynlib4.o:dynlib4.c:(.rdata$.refptr.H5E_PLUGIN_g[.refptr.H5E_PLUGIN_g]+0x0): undefined reference to `H5E_PLUGIN_g'
.libs/dynlib4.o:dynlib4.c:(.rdata$.refptr.H5E_CALLBACK_g[.refptr.H5E_CALLBACK_g]+0x0): undefined reference to `H5E_CALLBACK_g'
collect2: error: ld returned 1 exit status
make[1]: *** [Makefile:1265: libdynlib4.la] Error 1
make[1]: Leaving directory '/home/Kamran/hdf5-1.8.18/test'
make: *** [Makefile:586: all-recursive] Error 1



```

I eliminated the rest of statements and brought the last scripts containing the errors...

I would absolutely appreciate if anyone could help to solve it...
Thanks a lot,

---

### Post by coffeecat on 2017-03-05
Welcome to the forum.

You've posted in General Help which is for problems with the Ubuntu (or official flavours) operating system, yet you mention Cygwin which suggests you are using Windows as the base operating system. Please tell us more about your system so that we can ensure that your question is in the right place.

---

### Post by kciveng on 2017-03-05
Dear "coffeecat"

I searched for my problem in the forum to find the solution and I realized that some Cygwin problems were asked here before, So I thought that here is the right place.

Yes, I am using Cygwin on windows.(if it is not crime in Linux users' opinion ;) )

Many Thanks,

---

### Post by coffeecat on 2017-03-05
Not, not a crime at all! :)

You are very welcome to post here, but ubuntuforums might not be the best place for you. I would guess that not many members here would have experience of compiling stuff in Cygwin, or even of compiling hdf5 in Ubuntu. 

I've moved this thread to the Windows sub-forum, and edited your thread title to include a reference to Cygwin, in the hope that it might attract the person or people who could help you.

Good luck with finding a solution.

---

### Post by kciveng on 2017-03-05
Thanks a lot...

---

