---
title: "Netbeans C++ Problems"
date: 2011-03-02
forum: Ubuntu Dev Link Forum
---

### Post by Crockeo on 2011-03-02
I wasn't sure where to put this, as it's about Netbeans but a little bit about Ubuntu as well. Anyways, here it goes.

My problem is that #include <iostream> and #include <iostream.h> both don't work while using the g++ compiler in Netbeans. I don't really know much about Ubuntu as I just switched over from Vista, so I don't know whether it's because of something with Ubuntu (which I doubt), g++, or Netbeans.

---

### Post by cgroza on 2011-03-03
> **Crockeo said:**
> I wasn't sure where to put this, as it's about Netbeans but a little bit about Ubuntu as well. Anyways, here it goes.

My problem is that #include <iostream> and #include <iostream.h> both don't work while using the g++ compiler in Netbeans. I don't really know much about Ubuntu as I just switched over from Vista, so I don't know whether it's because of something with Ubuntu (which I doubt), g++, or Netbeans.

Does it spit any errors? That would me more than useful.

---

### Post by stchman on 2011-03-03
I just tried this on a Windows machine running Netbeans using gcc/g++ under Cygwin.  I am pleased to say it worked just fine.


[PHP]
/* 
 * File:   main.cpp
 * Author: Me
 *
 * Created on March 3, 2011, 5:42 PM
 */

#include <iostream>

using namespace std;

/*
 * 
 */
int main( int argc, char* argv[] )
{
    cout << "Hello World\n";
    return 0;
}

[/PHP]

---

### Post by kaspar_silas on 2011-03-03
Yip, you need give the error to get help. Shouldn't be difficult to solve after that.

---

### Post by stchman on 2011-03-06
I did some investigating and indeed there is a bug in Netbeans on 64 bit with >2 cores on a processor.

[http://netbeans.org/bugzilla/show_bug.cgi?id=184966](http://netbeans.org/bugzilla/show_bug.cgi?id=184966)

I personally encountered this.  If you uncheck the Show Profiling Indicators During Run in the Project Properties that appears to fix the problem.

---

### Post by daminkz on 2011-03-30
I don't think this fixes the main issue here.

The last time I installed Netbeans, it would refuse to find g++. Make sure you have g++ installed (sudo apt-get install g++) and then in the Netbeans options, make sure that the profiles are set to link to g++.

---

