---
title: "glib2 problems"
date: 2012-05-15
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cmccauley on 2012-05-15
Oh no, showstopper for me! I can't use Emacs. I suppose I can always fallback to vim !

;-)

Chris



root@chris-quantal:~# aptitude install emacs
The following NEW packages will be installed:
  emacs emacs23{a} emacs23-bin-common{a} emacs23-common{a} emacsen-common{a} libgif4{a} libm17n-0{a} libotf0{a} m17n-contrib{a} 
  m17n-db{a} 
0 packages upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 28.9 MB of archives. After unpacking 86.4 MB will be used.
The following packages have unmet dependencies:
 libglib2.0-0 : Breaks: emacs23 (< 23.4+1-3) but 23.3+1-1ubuntu9 is to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     emacs [Not Installed]                              
2)     emacs23 [Not Installed]                            



Accept this solution? [Y/n/q/?]

---

