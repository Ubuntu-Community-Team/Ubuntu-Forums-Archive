---
title: "How to uninstall particular python version if multiple versions on single computer"
date: 2017-09-23
forum: Ubuntu Application Development
---

### Post by rameshkjes on 2017-09-23
Hello, I am beginner in python therefore I am not getting how to remove one particular version of python if i have more than two on same computer. 

I executed this command to check number of python versions installed on ubuntu 14.04:

    ```
ls -l /usr/bin/python* 
```

It returns output on terminal as: 

    ```
lrwxrwxrwx 1 root root      16 Sep 12 13:48 /usr/bin/python -> /usr/bin/python3
    lrwxrwxrwx 1 root root       9 Sep  3  2016 /usr/bin/python2 -> python2.7
    -rwxr-xr-x 1 root root 3341384 Okt 26  2016 /usr/bin/python2.7
    lrwxrwxrwx 1 root root      33 Okt 26  2016 /usr/bin/python2.7-config -> x86_64-linux-gnu-python2.7-config
    lrwxrwxrwx 1 root root      16 Dez 21  2013 /usr/bin/python2-config -> python2.7-config
    lrwxrwxrwx 1 root root       9 Sep  3  2016 /usr/bin/python3 -> python3.4
    -rwxr-xr-x 2 root root 3693624 Nov 17  2016 /usr/bin/python3.4
    lrwxrwxrwx 1 root root      33 Nov 17  2016 /usr/bin/python3.4-config -> x86_64-linux-gnu-python3.4-config
    -rwxr-xr-x 2 root root 3693624 Nov 17  2016 /usr/bin/python3.4m
    lrwxrwxrwx 1 root root      34 Nov 17  2016 /usr/bin/python3.4m-config -> x86_64-linux-gnu-python3.4m-config
    -rwxr-xr-x 2 root root 4491872 Jul 20 11:13 /usr/bin/python3.6
    -rwxr-xr-x 2 root root 4491872 Jul 20 11:13 /usr/bin/python3.6m
    lrwxrwxrwx 1 root root      16 Mär 23  2014 /usr/bin/python3-config -> python3.4-config
    lrwxrwxrwx 1 root root      10 Sep  3  2016 /usr/bin/python3m -> python3.4m
    lrwxrwxrwx 1 root root      17 Mär 23  2014 /usr/bin/python3m-config -> python3.4m-config
    lrwxrwxrwx 1 root root      16 Dez 21  2013 /usrhttps://ubuntuforums.org//bin/python-config -> python2.7-config
    lrwxrwxrwx 1 root root      58 Feb 20  2014 /usr/bin/pythontex -> ../share/texlive/texmf-dist/scripts/pythontex/pythontex.py
    -rwxr-xr-x 1 root root     306 Feb 20  2014 /usr/bin/pythontex3
```

Now only I want to use python2.7 and  python3.4 so how can i remove rest others without affecting python2.7 and python3.4 

Thanks

---

### Post by ian-weisser on 2017-09-23
How you remove it depends upon how you installed it.
Please explain *in detail *how you originally installed the extra version of Python (3.6) that you now wish to remove.

---

