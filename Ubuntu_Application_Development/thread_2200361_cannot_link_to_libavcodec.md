---
title: "cannot link to libavcodec"
date: 2014-01-18
forum: Ubuntu Application Development
---

### Post by Andres Gonzalez on 2014-01-18
I am developing an application and want to use the libav library. I am having a problem with linking that is just baffling to me.

I built libav successfully. I configured it to --enable-pic and --enable-shared and it built without problems. It installed into /usr/local/lib with out problems. I can see that all of the libs are present in /usr/local/lib.

I can compile using the avcodec API without problems. All of the avcodec types are recognized so the libav headers files can be found without problems. 

When my build tries to link, I get many of the the following types of errors:

undefined reference to 'avcodec_version()'
undefined reference to 'avcodec_find_encoder(AVCodecID)'
    etc.....

I am linking with the -lavcodec linker option

I have built this code as root to see if it is a permissions problem. I have changed permissions and owner/group of the .so files to see it that is the problem. So it is not a permission/owner/group issue.

The confusing part is that the .so files are indeed found and read by the linker so it is not a path problem. This reason I know this, is that I added the libavformat library to the link options and the linker gave me a warning that the version of libavformat was different from the version of libavcodec.  Aside from this version issue, this tells me that the linker can indeed find and read the required .so file.

When I do an 'nm -g' on  libavcodec to show me the global exports, it indeed shows me that the routine avcodec_version(), and other API routines I am using, are indeed present in the text section and are considered global.

I am just baffled by this.  Anybody have an idea what might be the problem?

Thanks,

-Andres

PS. this is on  debian 7.1, g++ 4.7.2

---

### Post by steeldriver on 2014-01-18
What is your complete gcc / linker command line? are you sure you are listing the libraries in the required order?

---

### Post by Andres Gonzalez on 2014-01-18
Thank you for your reply.

Yes, I tried various orders of listing the lib but nothing fix it.  Then I found the problem. It was a C vs. C++ problem. To resolve it I did this:
 
 extern "C" {
#include <libavcodec/avcodec.h>
}

That resolved my problem. It compiles and links just fine.

Thanks again for taking the time to respond. Hopefully this will help someone in the future.

-Andres

---

