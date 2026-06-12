---
title: "Error trying to compile Objective-c++: 'cc1objplus' No such file or director"
date: 2013-01-18
forum: Ubuntu Application Development
---

### Post by SESteve on 2013-01-18
I'm trying to compile an Objective-C++ program in Ubuntu 12.04. I've done all of the following:

```
sudo apt-get -y install build-essential
sudo apt-get -y install gnustep
sudo apt-get install gobjc
sudo apt-get install gnustep-make
sudo apt-get install libgnustep-base-dev
```

When I try to compile with:
```
g++ test.mm -o test -lobjc -x objective-c++
```

I get this error:
```
g++: error trying to exec 'cc1objplus': execvp: No such file or directory
```

What step am I missing?

---

### Post by schragge on 2013-02-04
Have you *gobjc++* installed? If not
```
sudo apt-get install gobjc++
```

---

