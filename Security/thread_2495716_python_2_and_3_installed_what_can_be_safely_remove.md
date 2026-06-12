---
title: "python 2 and 3 installed what can be safely removed?"
date: 2024-02-28
forum: Security
---

### Post by pricesully-googlemail on 2024-02-28
we have a server and a variety of CVEs have been flagged for it
CVE-2022-45061, CVE-2022-37454, CVE-2022-42919, CVE-2023-24329, CVE-2015-20107, CVE-2021-28861

the server has at least 3 versions of python installed
the server is used solely as an ansible / rundeck provider

which versions of python are we safe to remove?


root@#####:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04.6 LTS"



root@#####:~# python -V
Python 2.7.18


root@#####:~# python2 -V
Python 2.7.18


root@#####:~# python3 -V
Python 3.9.5




root@#####:~# find / -type f -executable -iname 'python*' -exec file -i '{}' \; | awk -F: '/x-executable; charset=binary/ {print $1}' | xargs readlink -f | sort -u | xargs -I % sh -c 'echo -n "%: "; % -V'
/snap/core18/2796/usr/bin/python3.6: Python 3.6.9
/snap/core18/2796/usr/bin/python3.6m: Python 3.6.9
/snap/core18/2812/usr/bin/python3.6: Python 3.6.9
/snap/core18/2812/usr/bin/python3.6m: Python 3.6.9
/snap/core20/2105/usr/bin/python3.8: Python 3.8.10
/snap/core20/2182/usr/bin/python3.8: Python 3.8.10
/usr/bin/python3.8: Python 3.8.10
/usr/bin/python3.9: Python 3.9.5


all advice gratefully received

---

### Post by ajgreeny on 2024-02-28
My advice would be not to remove any of the python packages you currently have.

This forum is littered with threads from people who have done similar things and ended up with an unusable, or even in some cases an unbootable system.

By all means run ```
sudo apt autoremove
```  to clean away any unneeded packages but don't imagine you can mess around with python unless you know exactly what and why you are doing it!

---

### Post by ian-weisser on 2024-02-28
Ubuntu 20.04 shipped with Python 3.8.2 (deb package). Removing that version may destroy your system.
Everything else is optional (like Python 2.7)...unless you added it for a purpose.

Your 'find' command didn't find the python 2.7 you show installed. Nor any apt-installed version of Python3. What else didn't it find?

---

