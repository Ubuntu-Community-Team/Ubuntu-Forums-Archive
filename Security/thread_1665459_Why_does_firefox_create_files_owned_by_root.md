---
title: "Why does firefox create files owned by root?"
date: 2011-01-12
forum: Security
---

### Post by bilkay on 2011-01-12
I'm finding a lot of files in my .mozilla directory that are owned by root. Is this normal? If so, isn't it a security issue?

---

### Post by regala on 2011-01-12
> **bilkay said:**
> I'm finding a lot of files in my .mozilla directory that are owned by root. Is this normal? If so, isn't it a security issue?

how did you launch firefox ?
who did launch firefox ?

this is the only way it could happen (for example, a "sudo firefox" in a term may well do that). or firefox is setuid root and that is an horrible, scandalous bug and the packagers should be hung upside down for a whole month.

I think you did something like "sudo firefox" at one point in the past and it should be enough to do juste that.

br

---

### Post by uRock on 2011-01-12
Nothing in the .mozilla should be owned by root. Change the name to .mozilla1, then reopen firefox. Then to reinstate the old mozilla folder, you can delete the new that it makes, then rename the old one back to .mozilla.

Here is the results when I checked the file permissions of my .mozilla.
```
rabbit@ronnie-desktop:~/.mozilla$ ls -ail
total 28
2883737 drwxr-xr-x  6 rabbit rabbit 4096 2009-12-23 14:00 .
2883585 drwx------ 77 rabbit rabbit 4096 2011-01-12 08:07 ..
2885219 -rw-r--r--  1 rabbit rabbit  335 2009-09-09 15:56 appreg
2884207 drwxr-xr-x  6 rabbit rabbit 4096 2010-08-27 13:48 extensions
2883751 drwxr-xr-x  5 rabbit rabbit 4096 2009-12-23 14:00 firefox
2884211 drwxr-xr-x  4 rabbit rabbit 4096 2009-12-14 09:19 firefox.3.0-replaced
2884191 drwxr-xr-x  3 rabbit rabbit 4096 2009-09-09 15:58 sunbird
rabbit@ronnie-desktop:~/.mozilla$ cd ~/.mozilla/firefox
rabbit@ronnie-desktop:~/.mozilla/firefox$ ls -ail
total 24
2883751 drwxr-xr-x  5 rabbit rabbit 4096 2009-12-23 14:00 .
2883737 drwxr-xr-x  6 rabbit rabbit 4096 2009-12-23 14:00 ..
2884188 drwxr-xr-x  3 rabbit rabbit 4096 2010-12-10 09:36 Crash Reports
2883752 drwxr-xr-x  4 rabbit rabbit 4096 2009-11-08 12:00 firefox-3.5
2883886 drwxr-xr-x 13 rabbit rabbit 4096 2011-01-12 08:55 l9k89c9x.default
2884187 -rw-r--r--  1 rabbit rabbit   94 2009-09-09 10:06 profiles.ini
rabbit@ronnie-desktop:~/.mozilla/firefox$ cd ~/.mozilla/sunbird
rabbit@ronnie-desktop:~/.mozilla/sunbird$ ls -ail
total 16
2884191 drwxr-xr-x 3 rabbit rabbit 4096 2009-09-09 15:58 .
2883737 drwxr-xr-x 6 rabbit rabbit 4096 2009-12-23 14:00 ..
2884206 -rw-r--r-- 1 rabbit rabbit   94 2009-09-09 15:58 profiles.ini
2884192 drwxr-xr-x 4 rabbit rabbit 4096 2010-08-31 14:02 zd8l2unm.default
rabbit@ronnie-desktop:~/.mozilla/sunbird$ 

```

---

### Post by bilkay on 2011-01-12
> **regala said:**
> how did you launch firefox ?
who did launch firefox ?

this is the only way it could happen (for example, a "sudo firefox" in a term may well do that). or firefox is setuid root and that is an horrible, scandalous bug and the packagers should be hung upside down for a whole month.

I think you did something like "sudo firefox" at one point in the past and it should be enough to do juste that.

br
I NEVER ran firefox as root (or sudo)! Guaranteed!

None of the files are executable. They mostly seem crash-related.

```

$ cd .mozilla
$ find . -user root -exec ls -l {} \;

-rw-r--r-- 1 root root 0 2011-01-06 18:30 ./firefox/Crash Reports/submit.log
total 160
-rw------- 1 root root 155792 2011-01-06 08:17 2b0a0e90-3ebe-c39c-56684e1a-75fa5108.dmp
-rw------- 1 root root    458 2011-01-06 08:17 2b0a0e90-3ebe-c39c-56684e1a-75fa5108.extra
-rw------- 1 root root 458 2011-01-06 08:17 ./firefox/Crash Reports/pending/2b0a0e90-3ebe-c39c-56684e1a-75fa5108.extra
-rw------- 1 root root 155792 2011-01-06 08:17 ./firefox/Crash Reports/pending/2b0a0e90-3ebe-c39c-56684e1a-75fa5108.dmp
-rw-r--r-- 1 root root 55 2011-01-06 18:30 ./firefox/Crash Reports/crashreporter.ini
-rw------- 1 root root 10 2010-12-31 07:06 ./firefox/Crash Reports/InstallTime20101206122310
-rw-r--r-- 1 root root 10947 2011-01-12 11:17 ./firefox/utsgpb69.default/localstore.rdf
total 42420
-rw------- 1 root root   64200 2011-01-12 10:41 008C6605d01
-rw------- 1 root root   32676 2011-01-12 08:23 013DD5D3d01
-rw------- 1 root root   24618 2011-01-12 08:52 01807E19d01
-rw------- 1 root root   84274 2011-01-12 08:16 02B20AAAd01
-rw------- 1 root root  140905 2011-01-12 08:16 043D65B8d01
-rw------- 1 root root   24917 2011-01-12 08:52 05DFB104d01
-rw------- 1 root root   82070 2011-01-12 08:31 0609438Cd01
-rw------- 1 root root   20794 2011-01-12 08:15 067CA9AAd01
-rw------- 1 root root   27461 2011-01-12 08:34 07773364d01
-rw------- 1 root root   59034 2011-01-12 08:52 07C36DD8d01
-rw------- 1 root root   43508 2011-01-12 08:45 0873E4D5d01
-rw------- 1 root root   54075 2011-01-12 08:52 088849D2d01
-rw------- 1 root root   18665 2011-01-12 08:52 09F83EA9d01
-rw------- 1 root root   35436 2011-01-12 08:45 0BDB69DBd01
-rw------- 1 root root   18534 2011-01-12 08:46 0C14F1ECd01
-rw------- 1 root root  160251 2011-01-12 08:45 0CB79FF3d01
-rw------- 1 root root  197288 2011-01-12 08:16 0D8F852Dd01
-rw------- 1 root root   37266 2011-01-12 07:32 0EFF88C3d01
-rw------- 1 root root  222623 2011-01-12 08:16 0F587E81d01
-rw------- 1 root root  186231 2011-01-12 08:16 101C1691d01
-rw------- 1 root root   46923 2011-01-12 07:40 11703274d01
-rw------- 1 root root  177566 2011-01-12 08:16 1318026Bd01
-rw------- 1 root root   25070 2011-01-12 08:37 13506449d01
-rw------- 1 root root  241507 2011-01-12 08:16 13640C69d01
-rw------- 1 root root   34185 2011-01-12 08:32 139B8952d01
-rw------- 1 root root   20262 2011-01-12 08:31 13C9BB89d01
-rw------- 1 root root  134537 2011-01-12 08:16 141E3407d01
-rw------- 1 root root   24523 2011-01-12 08:45 14926420d01
-rw------- 1 root root   64801 2011-01-12 10:38 15507A27d01
-rw------- 1 root root   22889 2011-01-12 08:52 15B70554d01
-rw------- 1 root root   19444 2011-01-12 08:45 15B9B8B0d01
-rw------- 1 root root  166497 2011-01-12 08:16 15CC7083d01
-rw------- 1 root root   18973 2011-01-12 11:05 1694BFFFd01
-rw------- 1 root root   32308 2011-01-12 08:52 176514BAd01
-rw------- 1 root root   20090 2011-01-12 08:32 18927C8Cd01
-rw------- 1 root root  264521 2011-01-12 08:16 18C61CFEd01
-rw------- 1 root root  412135 2011-01-12 08:16 1A5B83E2d01
-rw------- 1 root root  132665 2011-01-12 08:16 1A6710A9d01
-rw------- 1 root root  145812 2011-01-12 08:16 1AA61305d01
-rw------- 1 root root   24165 2011-01-12 08:31 1B5714DCd01
-rw------- 1 root root   35941 2011-01-12 08:52 1B6C57E5d01
-rw------- 1 root root   19694 2011-01-12 07:18 1C4743D3d01
-rw------- 1 root root   18405 2011-01-12 08:34 1C7AFF14d01
-rw------- 1 root root   45545 2011-01-12 08:52 1D7241F9d01
-rw------- 1 root root  139977 2011-01-12 08:31 1D89ED92d01
-rw------- 1 root root  164529 2011-01-12 08:16 1DC86041d01
-rw------- 1 root root   51220 2011-01-12 08:37 1E39D46Dd01
-rw------- 1 root root   17596 2011-01-12 08:45 1E9D6FF1d01
-rw------- 1 root root   29569 2011-01-12 08:51 1ED16F06d01
-rw------- 1 root root   18844 2011-01-12 08:53 20CB0181d01
-rw------- 1 root root   35540 2011-01-12 08:17 220F95EEd01
-rw------- 1 root root  146686 2011-01-12 08:16 221C0141d01
-rw------- 1 root root  174097 2011-01-12 08:34 22AC22E2d01
-rw------- 1 root root   18602 2011-01-12 08:37 23039592d01
-rw------- 1 root root   85522 2011-01-12 08:16 23F76F17d01
-rw------- 1 root root   41717 2011-01-12 08:55 251D1D43d01
-rw------- 1 root root   47012 2011-01-12 08:16 27DA232Fd01
-rw------- 1 root root  176323 2011-01-12 08:16 27EDEBDCd01
-rw------- 1 root root   24972 2011-01-12 08:37 290C8768d01
-rw------- 1 root root   81414 2011-01-12 08:52 2991B31Ad01
-rw------- 1 root root   24168 2011-01-12 08:23 29A48185d01
-rw------- 1 root root   85457 2011-01-12 08:52 2AB26140d01
-rw------- 1 root root   60952 2011-01-12 08:45 2AF0941Fd01
-rw------- 1 root root   35540 2011-01-12 08:17 2B091E59d01
-rw------- 1 root root   34760 2011-01-12 08:15 2B7F7DF3d01
-rw------- 1 root root   39208 2011-01-12 08:52 2BBA97A3d01
-rw------- 1 root root   58787 2011-01-12 08:52 2C23EB09d01
-rw------- 1 root root   41172 2011-01-12 08:31 2C375DD2d01
-rw------- 1 root root  232607 2011-01-12 08:16 2C386EDCd01
-rw------- 1 root root  101772 2011-01-12 08:51 2D1526CBd01
-rw------- 1 root root  142070 2011-01-12 08:16 2DB11179d01
-rw------- 1 root root  144522 2011-01-12 08:16 2DC56ED3d01
-rw------- 1 root root   42026 2011-01-12 08:37 2E118472d01
-rw------- 1 root root   30904 2011-01-12 08:53 308EC962d01
-rw------- 1 root root   32933 2011-01-12 07:12 32B0EA89d01
-rw------- 1 root root   39273 2011-01-12 08:28 32F5D980d01
-rw------- 1 root root  149444 2011-01-12 08:16 3450972Bd01
-rw------- 1 root root  162866 2011-01-12 08:16 34A43D38d01
-rw------- 1 root root  250173 2011-01-12 08:16 34A9B28Cd01
-rw------- 1 root root   18378 2011-01-12 08:32 352CFB54d01
-rw------- 1 root root   26027 2011-01-12 13:14 354CCC4Cd01
-rw------- 1 root root  117730 2011-01-12 10:42 359AE592d01
-rw------- 1 root root   21397 2011-01-12 08:53 364C1B2Bd01
-rw------- 1 root root   37330 2011-01-12 08:31 367F6BBFd01
-rw------- 1 root root  258026 2011-01-12 08:16 36C10716d01
-rw------- 1 root root  225729 2011-01-12 08:16 389A1098d01
-rw------- 1 root root  252947 2011-01-12 08:16 3AD307ABd01
-rw------- 1 root root   84529 2011-01-12 08:31 3C15A934d01
-rw------- 1 root root   67958 2011-01-12 08:31 3C99BF63d01
-rw------- 1 root root   22664 2011-01-12 10:47 3D1A6F8Fd01
-rw------- 1 root root   36654 2011-01-12 08:34 3D481E14d01
-rw------- 1 root root   21971 2011-01-12 08:45 3D8CC51Ed01
-rw------- 1 root root   36469 2011-01-12 08:37 3DAD35B1d01
-rw------- 1 root root   36250 2011-01-12 08:32 3DDC2431d01
-rw------- 1 root root   31248 2011-01-12 08:31 3E0DE3B5d01
-rw------- 1 root root   31042 2011-01-12 08:52 3EFB0982d01
-rw------- 1 root root   19823 2011-01-12 08:51 3F4BF8D6d01
-rw------- 1 root root   63941 2011-01-12 08:18 3F9FABC6d01
-rw------- 1 root root   45246 2011-01-12 08:52 3FBD295Ed01
-rw------- 1 root root  169541 2011-01-12 08:16 4050E26Ed01
-rw------- 1 root root   21771 2011-01-12 08:23 40D6E982d01
-rw------- 1 root root  921654 2011-01-12 08:52 41465795d01
-rw------- 1 root root   32241 2011-01-12 09:02 41A79BA4d01
-rw------- 1 root root   71890 2011-01-12 08:31 426BE276d01
-rw------- 1 root root  170741 2011-01-12 08:16 4380D42Bd01
-rw------- 1 root root   20559 2011-01-12 08:35 438F9D80d01
-rw------- 1 root root   19826 2011-01-12 09:02 43F57918d01
-rw------- 1 root root   18974 2011-01-12 10:23 451676CEd01
-rw------- 1 root root  133208 2011-01-12 08:16 45DA5E5Dd01
-rw------- 1 root root   19820 2011-01-12 08:31 47A80D4Fd01
-rw------- 1 root root   57276 2011-01-12 08:34 47C73261d01
-rw------- 1 root root   22933 2011-01-12 08:32 4816696Fd01
-rw------- 1 root root  144696 2011-01-12 08:34 48C348ADd01
-rw------- 1 root root   22567 2011-01-12 08:39 48E47F84d01
-rw------- 1 root root  170517 2011-01-12 08:16 4A385565d01
-rw------- 1 root root   55272 2011-01-12 08:34 4A779BF7d01
-rw------- 1 root root   33533 2011-01-12 08:34 4AF28467d01
-rw------- 1 root root  196341 2011-01-12 08:16 4AFC87C3d01
-rw------- 1 root root  160123 2011-01-12 08:16 4B18F759d01
-rw------- 1 root root  181752 2011-01-12 08:16 4BEC2207d01
-rw------- 1 root root   28118 2011-01-12 08:45 4DA63BB7d01
-rw------- 1 root root   36012 2011-01-12 08:52 4DE77415d01
-rw------- 1 root root   55699 2011-01-12 10:55 4F6E7992d01
-rw------- 1 root root   21219 2011-01-12 08:34 4F80A4ABd01
-rw------- 1 root root   19558 2011-01-12 09:02 4F893A57d01
-rw------- 1 root root   73425 2011-01-12 10:47 4FD99B00d01
-rw------- 1 root root  871374 2011-01-12 08:45 4FDAC4BAd01
-rw------- 1 root root   83997 2011-01-12 08:34 4FE07ECEd01
-rw------- 1 root root   58941 2011-01-12 08:45 508C9BDBd01
-rw------- 1 root root   21101 2011-01-12 08:34 51727FB8d01
-rw------- 1 root root   21798 2011-01-12 08:23 51732E99d01
-rw------- 1 root root   40317 2011-01-12 08:45 51C12069d01
-rw------- 1 root root   83542 2011-01-12 08:31 54D4D681d01
-rw------- 1 root root   18602 2011-01-12 08:37 553C70D9d01
-rw------- 1 root root   59593 2011-01-12 08:52 554F4D16d01
-rw------- 1 root root   46046 2011-01-12 08:52 55E2AAF9d01
-rw------- 1 root root  138439 2011-01-12 08:52 56102FEBd01
-rw------- 1 root root   43757 2011-01-12 08:34 574C67C7d01
-rw------- 1 root root  145558 2011-01-12 08:52 592E834Dd01
-rw------- 1 root root   27197 2011-01-12 08:50 59A74190d01
-rw------- 1 root root   84363 2011-01-12 08:39 5C592673d01
-rw------- 1 root root  123049 2011-01-12 08:16 5C6B411Ed01
-rw------- 1 root root  197992 2011-01-12 08:16 5DF612BEd01
-rw------- 1 root root  141977 2011-01-12 08:16 5EF8E5A9d01
-rw------- 1 root root   22535 2011-01-12 08:23 5F007E41d01
-rw------- 1 root root   18994 2011-01-12 09:02 60AA04C3d01
-rw------- 1 root root   17454 2011-01-12 08:53 60DCF185d01
-rw------- 1 root root   46079 2011-01-12 08:31 61310760d01
-rw------- 1 root root   53143 2011-01-12 10:43 627FBF74d01
-rw------- 1 root root  144514 2011-01-12 08:16 630BB68Fd01
-rw------- 1 root root   20312 2011-01-12 08:45 63923D8Bd01
-rw------- 1 root root   33231 2011-01-12 08:39 64DCB567d01
-rw------- 1 root root   25405 2011-01-12 09:02 654F93DCd01
-rw------- 1 root root   27395 2011-01-12 09:02 65E8D3B0d01
-rw------- 1 root root  271000 2011-01-12 08:31 67D148DDd01
-rw------- 1 root root  176742 2011-01-12 08:16 68CD9FF0d01
-rw------- 1 root root   29191 2011-01-12 09:02 68F06A24d01
-rw------- 1 root root   42333 2011-01-12 08:37 69104025d01
-rw------- 1 root root   20014 2011-01-12 08:34 6A101156d01
-rw------- 1 root root   27395 2011-01-12 09:02 6A1CE479d01
-rw------- 1 root root   70113 2011-01-12 08:52 6A48A5C2d01
-rw------- 1 root root   91133 2011-01-12 08:52 6A8CCB80d01
-rw------- 1 root root   57369 2011-01-12 08:32 6B795FDCd01
-rw------- 1 root root   28193 2011-01-12 08:53 6BCC95ADd01
-rw------- 1 root root   63949 2011-01-12 08:31 6BDEE08Cd01
-rw------- 1 root root   16702 2011-01-12 08:34 6C4C3CE5d01
-rw------- 1 root root   19782 2011-01-12 08:52 6C6105DBd01
-rw------- 1 root root   47869 2011-01-12 08:45 6C8D663Fd01
-rw------- 1 root root   43416 2011-01-12 09:02 6EB7D82Ed01
-rw------- 1 root root   16720 2011-01-12 08:53 6F32C5CFd01
-rw------- 1 root root  130097 2011-01-12 08:16 6F5F4DFEd01
-rw------- 1 root root  216479 2011-01-12 08:16 6FA60853d01
-rw------- 1 root root   16669 2011-01-12 11:05 6FDDB4D2d01
-rw------- 1 root root   26343 2011-01-12 08:39 70D26250d01
-rw------- 1 root root   30781 2011-01-12 08:37 714D1B5Fd01
-rw------- 1 root root  127997 2011-01-12 08:16 71B33273d01
-rw------- 1 root root   51724 2011-01-12 10:41 72752C79d01
-rw------- 1 root root   70468 2011-01-12 08:31 72E5BEA7d01
-rw------- 1 root root  163131 2011-01-12 08:16 73EC61D4d01
-rw------- 1 root root   16884 2011-01-12 09:02 7537AA79d01
-rw------- 1 root root   29984 2011-01-12 07:53 76316266d01
-rw------- 1 root root   20431 2011-01-12 09:02 770A8FA0d01
-rw------- 1 root root   24678 2011-01-12 08:37 7833D82Dd01
-rw------- 1 root root   60293 2011-01-12 08:34 788D4EBEd01
-rw------- 1 root root  190575 2011-01-12 08:16 78BD8F4Dd01
-rw------- 1 root root   26482 2011-01-12 08:23 7913F57Dd01
-rw------- 1 root root  216905 2011-01-12 08:31 79C9AEAEd01
-rw------- 1 root root   55774 2011-01-12 08:24 79DBAAABd01
-rw------- 1 root root   27197 2011-01-12 08:47 7AA8DF7Fd01
-rw------- 1 root root   17371 2011-01-12 07:40 7ACBB7C3d01
-rw------- 1 root root   76288 2011-01-12 09:02 7DBCA9E8d01
-rw------- 1 root root   34803 2011-01-12 08:45 7ED1FA02d01
-rw------- 1 root root   18421 2011-01-12 07:06 80B036F4d01
-rw------- 1 root root  133774 2011-01-12 08:16 82F8ED18d01
-rw------- 1 root root  101754 2011-01-12 08:52 83B81C7Cd01
-rw------- 1 root root   30624 2011-01-12 08:31 84A9CA9Fd01
-rw------- 1 root root  179110 2011-01-12 08:16 85101E0Dd01
-rw------- 1 root root   28391 2011-01-12 08:31 87951EFFd01
-rw------- 1 root root   19820 2011-01-12 08:52 89228A9Dd01
-rw------- 1 root root   36679 2011-01-12 09:02 895C87C6d01
-rw------- 1 root root   36871 2011-01-12 08:23 895DFCA2d01
-rw------- 1 root root   40236 2011-01-12 08:35 898A447Ed01
-rw------- 1 root root   75834 2011-01-12 08:45 8AD48EF1d01
-rw------- 1 root root  174889 2011-01-12 08:16 8B009BE0d01
-rw------- 1 root root  116880 2011-01-12 08:16 8B158E62d01
-rw------- 1 root root   45928 2011-01-12 08:23 8B57F6E6d01
-rw------- 1 root root  249444 2011-01-12 08:16 8CB693A7d01
-rw------- 1 root root  166821 2011-01-12 08:16 8D37DE9Ad01
-rw------- 1 root root  103604 2011-01-12 08:34 8D5209BAd01
-rw------- 1 root root   27313 2011-01-12 08:52 8DDBF755d01
-rw------- 1 root root  235588 2011-01-12 08:16 8E48F991d01
-rw------- 1 root root   29581 2011-01-12 08:45 8EA64124d01
-rw------- 1 root root   27306 2011-01-12 08:24 903505D5d01
-rw------- 1 root root  129067 2011-01-12 08:16 911E67FCd01
-rw------- 1 root root   20399 2011-01-12 08:23 9175F601d01
-rw------- 1 root root   36078 2011-01-12 08:39 91ADBA10d01
-rw------- 1 root root   27441 2011-01-12 08:15 91B63165d01
-rw------- 1 root root   51808 2011-01-12 08:34 92D08D6Cd01
-rw------- 1 root root  170252 2011-01-12 08:16 92F9C064d01
-rw------- 1 root root   19630 2011-01-12 08:45 93281CA4d01
-rw------- 1 root root   22203 2011-01-12 08:37 933EBD21d01
-rw------- 1 root root   52040 2011-01-12 13:11 93898CACd01
-rw------- 1 root root   56186 2011-01-12 10:38 94862D8Ed01
-rw------- 1 root root  138979 2011-01-12 08:52 956F5806d01
-rw------- 1 root root  147966 2011-01-12 08:52 960CBC66d01
-rw------- 1 root root  301079 2011-01-12 08:16 978E6B48d01
-rw------- 1 root root  191060 2011-01-12 08:16 98490367d01
-rw------- 1 root root   78146 2011-01-12 08:52 98B6EA7Ad01
-rw------- 1 root root   64985 2011-01-12 08:31 9931E896d01
-rw------- 1 root root   28028 2011-01-12 08:32 997C8021d01
-rw------- 1 root root  232739 2011-01-12 08:16 99D4292Dd01
-rw------- 1 root root   19553 2011-01-12 08:45 99F64200d01
-rw------- 1 root root  167613 2011-01-12 08:16 9A54EFDAd01
-rw------- 1 root root   17785 2011-01-12 08:39 9AB8DB54d01
-rw------- 1 root root   29952 2011-01-12 08:45 9BB9E28Ad01
-rw------- 1 root root  148576 2011-01-12 08:16 9BF3C979d01
-rw------- 1 root root   17322 2011-01-12 08:37 9C11657Ed01
-rw------- 1 root root   74101 2011-01-12 08:52 9D2C41DDd01
-rw------- 1 root root   54386 2011-01-12 08:52 9D48C967d01
-rw------- 1 root root   38106 2011-01-12 08:34 9DC41B20d01
-rw------- 1 root root   31358 2011-01-12 08:45 9DF443F4d01
-rw------- 1 root root   27107 2011-01-12 08:45 9E1E614Ed01
-rw------- 1 root root   97264 2011-01-12 08:16 9F03F64Ed01
-rw------- 1 root root  157532 2011-01-12 08:52 9F499191d01
-rw------- 1 root root   54877 2011-01-12 08:34 9F53A0F1d01
-rw------- 1 root root   25359 2011-01-12 08:52 A02AB491d01
-rw------- 1 root root   36225 2011-01-12 08:52 A2F273D4d01
-rw------- 1 root root   49085 2011-01-12 08:51 A38224C0d01
-rw------- 1 root root   30782 2011-01-12 08:23 A3AD93AFd01
-rw------- 1 root root   28571 2011-01-12 08:32 A3C05D45d01
-rw------- 1 root root   27243 2011-01-12 08:15 A4634172d01
-rw------- 1 root root   48907 2011-01-12 08:51 A5F9CEA7d01
-rw------- 1 root root  129906 2011-01-12 08:16 A73AAFAFd01
-rw------- 1 root root   27540 2011-01-12 10:38 A7531EE3d01
-rw------- 1 root root  150079 2011-01-12 08:35 A8A0A9BCd01
-rw------- 1 root root  182682 2011-01-12 08:16 A8F91D72d01
-rw------- 1 root root   36477 2011-01-12 08:39 A921D91Bd01
-rw------- 1 root root   38625 2011-01-12 08:23 A9393A13d01
-rw------- 1 root root   18272 2011-01-12 08:45 AB18B4C2d01
-rw------- 1 root root   20316 2011-01-12 09:02 AB31F1CAd01
-rw------- 1 root root   20120 2011-01-12 08:31 AD5D7812d01
-rw------- 1 root root  143382 2011-01-12 08:16 AD921404d01
-rw------- 1 root root   57812 2011-01-12 08:52 AEEAABC2d01
-rw------- 1 root root  197243 2011-01-12 08:16 AFB35F92d01
-rw------- 1 root root   32061 2011-01-12 08:35 AFBE957Ed01
-rw------- 1 root root   44809 2011-01-12 08:52 AFF9A10Cd01
-rw------- 1 root root   74007 2011-01-12 08:37 B132C028d01
-rw------- 1 root root   17300 2011-01-12 08:37 B140CF3Ed01
-rw------- 1 root root  119957 2011-01-12 10:39 B23073D8d01
-rw------- 1 root root   89444 2011-01-12 13:10 B3439DCCd01
-rw------- 1 root root   25583 2011-01-12 08:45 B34D9275d01
-rw------- 1 root root   33827 2011-01-12 08:46 B39BC657d01
-rw------- 1 root root   48839 2011-01-12 08:39 B3C577D1d01
-rw------- 1 root root   99331 2011-01-12 08:16 B40ABDCCd01
-rw------- 1 root root   24656 2011-01-12 08:52 B4577F7Ad01
-rw------- 1 root root   17629 2011-01-12 08:45 B4A9AADDd01
-rw------- 1 root root   66201 2011-01-12 08:53 B5C0D421d01
-rw------- 1 root root  107669 2011-01-12 08:16 B8DEF8A3d01
-rw------- 1 root root  109470 2011-01-12 08:16 B9345882d01
-rw------- 1 root root  159577 2011-01-12 08:16 B9D8BF92d01
-rw------- 1 root root  156707 2011-01-12 08:16 BA56CB21d01
-rw------- 1 root root   54936 2011-01-12 08:31 BA7C4F86d01
-rw------- 1 root root   17305 2011-01-12 09:04 BB29CB54d01
-rw------- 1 root root   46336 2011-01-12 08:45 BCB055A7d01
-rw------- 1 root root  178213 2011-01-12 08:16 BCB724AAd01
-rw------- 1 root root   23960 2011-01-12 08:23 BD7015C7d01
-rw------- 1 root root  119030 2011-01-12 08:16 BE726FDEd01
-rw------- 1 root root  187592 2011-01-12 08:16 BEC05087d01
-rw------- 1 root root   60093 2011-01-12 08:52 BF1D4756d01
-rw------- 1 root root   55592 2011-01-12 08:34 C01FF91Bd01
-rw------- 1 root root   35540 2011-01-12 08:18 C0282B1Dd01
-rw------- 1 root root   21356 2011-01-12 08:31 C09F71A1d01
-rw------- 1 root root   47317 2011-01-12 08:51 C2B58FBCd01
-rw------- 1 root root   23652 2011-01-12 08:34 C4341D22d01
-rw------- 1 root root  280218 2011-01-12 08:45 C4B083EDd01
-rw------- 1 root root   68584 2011-01-12 08:45 C59FE7ACd01
-rw------- 1 root root   18371 2011-01-12 08:53 C75ADE41d01
-rw------- 1 root root  216010 2011-01-12 08:16 C8A194AFd01
-rw------- 1 root root   64613 2011-01-12 08:31 C8FBE89Ad01
-rw------- 1 root root   23664 2011-01-12 08:17 C9BC374Ed01
-rw------- 1 root root   73212 2011-01-12 10:48 CA2D3EE0d01
-rw------- 1 root root 2249219 2011-01-12 13:14 _CACHE_001_
-rw------- 1 root root 2417818 2011-01-12 13:14 _CACHE_002_
-rw------- 1 root root 5894748 2011-01-12 13:14 _CACHE_003_
-rw------- 1 root root   65812 2011-01-12 13:10 _CACHE_MAP_
-rw------- 1 root root   29416 2011-01-12 08:37 CB420BD2d01
-rw------- 1 root root   41356 2011-01-12 09:02 CB855CB7d01
-rw------- 1 root root  172655 2011-01-12 08:16 CCBE393Fd01
-rw------- 1 root root   87797 2011-01-12 08:34 CD4913BDd01
-rw------- 1 root root   33322 2011-01-12 08:31 CD79396Fd01
-rw------- 1 root root   24678 2011-01-12 08:37 CE6E2E3Ad01
-rw------- 1 root root   29448 2011-01-12 08:37 CEEF1936d01
-rw------- 1 root root  143204 2011-01-12 08:16 CF10CAF6d01
-rw------- 1 root root  136004 2011-01-12 08:16 CFD822CDd01
-rw------- 1 root root   20777 2011-01-12 10:55 D0AB160Ad01
-rw------- 1 root root  106697 2011-01-12 08:31 D0FD447Cd01
-rw------- 1 root root   60244 2011-01-12 08:31 D1C4D4F1d01
-rw------- 1 root root   38002 2011-01-12 08:31 D1DF5EB5d01
-rw------- 1 root root 1106527 2011-01-12 08:45 D266BF58d01
-rw------- 1 root root   47267 2011-01-12 10:22 D3573611d01
-rw------- 1 root root   20685 2011-01-12 08:45 D3BCF2B4d01
-rw------- 1 root root   17625 2011-01-12 08:45 D4002D0Fd01
-rw------- 1 root root   25888 2011-01-12 08:32 D6042E29d01
-rw------- 1 root root   36055 2011-01-12 08:31 D61D29ACd01
-rw------- 1 root root   43057 2011-01-12 08:31 D75CE696d01
-rw------- 1 root root  211058 2011-01-12 08:31 D879472Ed01
-rw------- 1 root root   55948 2011-01-12 09:02 D88B8212d01
-rw------- 1 root root  134325 2011-01-12 08:45 D8B64340d01
-rw------- 1 root root   22101 2011-01-12 08:45 D8CC7647d01
-rw------- 1 root root  135719 2011-01-12 08:45 D9F0FFDDd01
-rw------- 1 root root   19354 2011-01-12 08:15 DA72EB27d01
-rw------- 1 root root   68566 2011-01-12 08:35 DB072C03d01
-rw------- 1 root root   45042 2011-01-12 08:45 DB893D97d01
-rw------- 1 root root   21704 2011-01-12 08:39 DCF30E0Ad01
-rw------- 1 root root   57254 2011-01-12 08:15 DD55C2DFd01
-rw------- 1 root root   24175 2011-01-12 08:15 DF08CDC4d01
-rw------- 1 root root  225271 2011-01-12 08:45 DFC513B8d01
-rw------- 1 root root   73521 2011-01-12 08:52 DFD1E425d01
-rw------- 1 root root   24785 2011-01-12 08:23 E01D19EFd01
-rw------- 1 root root   31118 2011-01-12 08:32 E167CD00d01
-rw------- 1 root root   94715 2011-01-12 10:39 E1C0D919d01
-rw------- 1 root root   27197 2011-01-12 08:52 E4DB75E3d01
-rw------- 1 root root   23542 2011-01-12 07:07 E6BE7911d01
-rw------- 1 root root  151390 2011-01-12 08:52 E7943D8Cd01
-rw------- 1 root root   19820 2011-01-12 08:32 E7A0B46Ed01
-rw------- 1 root root   28397 2011-01-12 08:56 E88F4F09d01
-rw------- 1 root root   19823 2011-01-12 08:56 E9A5DE2Dd01
-rw------- 1 root root  162987 2011-01-12 08:16 E9C55D7Ad01
-rw------- 1 root root   49667 2011-01-12 08:17 E9C5D536d01
-rw------- 1 root root   31012 2011-01-12 08:53 E9DE318Ad01
-rw------- 1 root root   43474 2011-01-12 08:17 EA8EF8E9d01
-rw------- 1 root root   45135 2011-01-12 08:17 EB86EC42d01
-rw------- 1 root root   17756 2011-01-12 08:45 ED36E86Ad01
-rw------- 1 root root   30461 2011-01-12 09:02 EDCF7E01d01
-rw------- 1 root root   22901 2011-01-12 08:34 EEB92B0Fd01
-rw------- 1 root root   20166 2011-01-12 08:24 EED26515d01
-rw------- 1 root root   95550 2011-01-12 13:14 EF99A6B1d01
-rw------- 1 root root   50247 2011-01-12 08:51 EFADB720d01
-rw------- 1 root root   93325 2011-01-12 08:31 EFDDCFCEd01
-rw------- 1 root root  275283 2011-01-12 08:16 F0D0EA12d01
-rw------- 1 root root  143157 2011-01-12 08:16 F279FBD2d01
-rw------- 1 root root  134321 2011-01-12 08:16 F2A8A4FEd01
-rw------- 1 root root   53058 2011-01-12 08:31 F2B016D3d01
-rw------- 1 root root  153875 2011-01-12 08:16 F2D0AC81d01
-rw------- 1 root root   28423 2011-01-12 08:39 F30E3123d01
-rw------- 1 root root   36690 2011-01-12 08:39 F3FDFFAFd01
-rw------- 1 root root   36750 2011-01-12 08:52 F425EA50d01
-rw------- 1 root root   33223 2011-01-12 08:23 F438D034d01
-rw------- 1 root root   23839 2011-01-12 08:45 F443840Ed01
-rw------- 1 root root   26379 2011-01-12 08:45 F5305D8Cd01
-rw------- 1 root root  104275 2011-01-12 08:45 F56CFBF0d01
-rw------- 1 root root   50835 2011-01-12 08:52 F66BB4A7d01
-rw------- 1 root root   37749 2011-01-12 08:34 F9AB0422d01
-rw------- 1 root root   21753 2011-01-12 08:45 FA1E0B12d01
-rw------- 1 root root  192385 2011-01-12 08:16 FA7DA057d01
-rw------- 1 root root  232343 2011-01-12 08:16 FA7E6961d01
-rw------- 1 root root  184103 2011-01-12 08:16 FAA2AA85d01
-rw------- 1 root root  391575 2011-01-12 08:45 FABD44A1d01
-rw------- 1 root root   22157 2011-01-12 08:52 FAF55C61d01
-rw------- 1 root root   36989 2011-01-12 08:31 FBF243F9d01
-rw------- 1 root root  170022 2011-01-12 08:16 FD053170d01
-rw------- 1 root root   56604 2011-01-12 08:23 FD475791d01
-rw------- 1 root root   46797 2011-01-12 08:52 FD5C9F88d01
-rw------- 1 root root  172195 2011-01-12 08:52 FE01328Dd01
-rw------- 1 root root   55087 2011-01-12 13:14 FE481DACd01
-rw------- 1 root root 55592 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/C01FF91Bd01
-rw------- 1 root root 116880 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/8B158E62d01
-rw------- 1 root root 123049 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/5C6B411Ed01
-rw------- 1 root root 22157 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/FAF55C61d01
-rw------- 1 root root 23960 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/BD7015C7d01
-rw------- 1 root root 41356 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/CB855CB7d01
-rw------- 1 root root 36477 2011-01-12 08:39 ./firefox/utsgpb69.default/Cache/A921D91Bd01
-rw------- 1 root root 54386 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/9D48C967d01
-rw------- 1 root root 138439 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/56102FEBd01
-rw------- 1 root root 921654 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/41465795d01
-rw------- 1 root root 34185 2011-01-12 08:32 ./firefox/utsgpb69.default/Cache/139B8952d01
-rw------- 1 root root 143204 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/CF10CAF6d01
-rw------- 1 root root 16884 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/7537AA79d01
-rw------- 1 root root 17785 2011-01-12 08:39 ./firefox/utsgpb69.default/Cache/9AB8DB54d01
-rw------- 1 root root 45928 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/8B57F6E6d01
-rw------- 1 root root 160123 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/4B18F759d01
-rw------- 1 root root 55272 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/4A779BF7d01
-rw------- 1 root root 37330 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/367F6BBFd01
-rw------- 1 root root 45135 2011-01-12 08:17 ./firefox/utsgpb69.default/Cache/EB86EC42d01
-rw------- 1 root root 60293 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/788D4EBEd01
-rw------- 1 root root 235588 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/8E48F991d01
-rw------- 1 root root 26343 2011-01-12 08:39 ./firefox/utsgpb69.default/Cache/70D26250d01
-rw------- 1 root root 22203 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/933EBD21d01
-rw------- 1 root root 134537 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/141E3407d01
-rw------- 1 root root 170022 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/FD053170d01
-rw------- 1 root root 119030 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/BE726FDEd01
-rw------- 1 root root 36012 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/4DE77415d01
-rw------- 1 root root 82070 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/0609438Cd01
-rw------- 1 root root 107669 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/B8DEF8A3d01
-rw------- 1 root root 81414 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/2991B31Ad01
-rw------- 1 root root 134321 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/F2A8A4FEd01
-rw------- 1 root root 32308 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/176514BAd01
-rw------- 1 root root 74007 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/B132C028d01
-rw------- 1 root root 19444 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/15B9B8B0d01
-rw------- 1 root root 19558 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/4F893A57d01
-rw------- 1 root root 182682 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/A8F91D72d01
-rw------- 1 root root 20777 2011-01-12 10:55 ./firefox/utsgpb69.default/Cache/D0AB160Ad01
-rw------- 1 root root 50835 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/F66BB4A7d01
-rw------- 1 root root 84363 2011-01-12 08:39 ./firefox/utsgpb69.default/Cache/5C592673d01
-rw------- 1 root root 28118 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/4DA63BB7d01
-rw------- 1 root root 94715 2011-01-12 10:39 ./firefox/utsgpb69.default/Cache/E1C0D919d01
-rw------- 1 root root 46923 2011-01-12 07:40 ./firefox/utsgpb69.default/Cache/11703274d01
-rw------- 1 root root 23839 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/F443840Ed01
-rw------- 1 root root 101754 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/83B81C7Cd01
-rw------- 1 root root 54936 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/BA7C4F86d01
-rw------- 1 root root 24168 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/29A48185d01
-rw------- 1 root root 117730 2011-01-12 10:42 ./firefox/utsgpb69.default/Cache/359AE592d01
-rw------- 1 root root 40317 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/51C12069d01
-rw------- 1 root root 190575 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/78BD8F4Dd01
-rw------- 1 root root 47317 2011-01-12 08:51 ./firefox/utsgpb69.default/Cache/C2B58FBCd01
-rw------- 1 root root 19630 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/93281CA4d01
-rw------- 1 root root 17371 2011-01-12 07:40 ./firefox/utsgpb69.default/Cache/7ACBB7C3d01
-rw------- 1 root root 179110 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/85101E0Dd01
-rw------- 1 root root 24785 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/E01D19EFd01
-rw------- 1 root root 63949 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/6BDEE08Cd01
-rw------- 1 root root 27197 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/E4DB75E3d01
-rw------- 1 root root 21771 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/40D6E982d01
-rw------- 1 root root 31012 2011-01-12 08:53 ./firefox/utsgpb69.default/Cache/E9DE318Ad01
-rw------- 1 root root 28423 2011-01-12 08:39 ./firefox/utsgpb69.default/Cache/F30E3123d01
-rw------- 1 root root 22535 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/5F007E41d01
-rw------- 1 root root 75834 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/8AD48EF1d01
-rw------- 1 root root 33827 2011-01-12 08:46 ./firefox/utsgpb69.default/Cache/B39BC657d01
-rw------- 1 root root 73212 2011-01-12 10:48 ./firefox/utsgpb69.default/Cache/CA2D3EE0d01
-rw------- 1 root root 129067 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/911E67FCd01
-rw------- 1 root root 84529 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/3C15A934d01
-rw------- 1 root root 36469 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/3DAD35B1d01
-rw------- 1 root root 27395 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/65E8D3B0d01
-rw------- 1 root root 28193 2011-01-12 08:53 ./firefox/utsgpb69.default/Cache/6BCC95ADd01
-rw------- 1 root root 144522 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/2DC56ED3d01
-rw------- 1 root root 64985 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/9931E896d01
-rw------- 1 root root 17596 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/1E9D6FF1d01
-rw------- 1 root root 35540 2011-01-12 08:17 ./firefox/utsgpb69.default/Cache/2B091E59d01
-rw------- 1 root root 211058 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/D879472Ed01
-rw------- 1 root root 26482 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/7913F57Dd01
-rw------- 1 root root 20014 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/6A101156d01
-rw------- 1 root root 134325 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/D8B64340d01
-rw------- 1 root root 47869 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/6C8D663Fd01
-rw------- 1 root root 99331 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/B40ABDCCd01
-rw------- 1 root root 19782 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/6C6105DBd01
-rw------- 1 root root 36750 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/F425EA50d01
-rw------- 1 root root 19354 2011-01-12 08:15 ./firefox/utsgpb69.default/Cache/DA72EB27d01
-rw------- 1 root root 144696 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/48C348ADd01
-rw------- 1 root root 36989 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/FBF243F9d01
-rw------- 1 root root 31118 2011-01-12 08:32 ./firefox/utsgpb69.default/Cache/E167CD00d01
-rw------- 1 root root 24165 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/1B5714DCd01
-rw------- 1 root root 22567 2011-01-12 08:39 ./firefox/utsgpb69.default/Cache/48E47F84d01
-rw------- 1 root root 46797 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/FD5C9F88d01
-rw------- 1 root root 51724 2011-01-12 10:41 ./firefox/utsgpb69.default/Cache/72752C79d01
-rw------- 1 root root 181752 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/4BEC2207d01
-rw------- 1 root root 20166 2011-01-12 08:24 ./firefox/utsgpb69.default/Cache/EED26515d01
-rw------- 1 root root 59593 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/554F4D16d01
-rw------- 1 root root 64801 2011-01-12 10:38 ./firefox/utsgpb69.default/Cache/15507A27d01
-rw------- 1 root root 177566 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/1318026Bd01
-rw------- 1 root root 56604 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/FD475791d01
-rw------- 1 root root 33223 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/F438D034d01
-rw------- 1 root root 28397 2011-01-12 08:56 ./firefox/utsgpb69.default/Cache/E88F4F09d01
-rw------- 1 root root 170517 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/4A385565d01
-rw------- 1 root root 176742 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/68CD9FF0d01
-rw------- 1 root root 43474 2011-01-12 08:17 ./firefox/utsgpb69.default/Cache/EA8EF8E9d01
-rw------- 1 root root 103604 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/8D5209BAd01
-rw------- 1 root root 71890 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/426BE276d01
-rw------- 1 root root 167613 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/9A54EFDAd01
-rw------- 1 root root 145812 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/1AA61305d01
-rw------- 1 root root 35941 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/1B6C57E5d01
-rw------- 1 root root 17756 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/ED36E86Ad01
-rw------- 1 root root 28028 2011-01-12 08:32 ./firefox/utsgpb69.default/Cache/997C8021d01
-rw------- 1 root root 60093 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/BF1D4756d01
-rw------- 1 root root 43757 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/574C67C7d01
-rw------- 1 root root 42026 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/2E118472d01
-rw------- 1 root root 192385 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/FA7DA057d01
-rw------- 1 root root 85457 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/2AB26140d01
-rw------- 1 root root 70468 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/72E5BEA7d01
-rw------- 1 root root 27306 2011-01-12 08:24 ./firefox/utsgpb69.default/Cache/903505D5d01
-rw------- 1 root root 216905 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/79C9AEAEd01
-rw------- 1 root root 73425 2011-01-12 10:47 ./firefox/utsgpb69.default/Cache/4FD99B00d01
-rw------- 1 root root 76288 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/7DBCA9E8d01
-rw------- 1 root root 29984 2011-01-12 07:53 ./firefox/utsgpb69.default/Cache/76316266d01
-rw------- 1 root root 66201 2011-01-12 08:53 ./firefox/utsgpb69.default/Cache/B5C0D421d01
-rw------- 1 root root 67958 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/3C99BF63d01
-rw------- 1 root root 24656 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/B4577F7Ad01
-rw------- 1 root root 27243 2011-01-12 08:15 ./firefox/utsgpb69.default/Cache/A4634172d01
-rw------- 1 root root 138979 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/956F5806d01
-rw------- 1 root root 250173 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/34A9B28Cd01
-rw------- 1 root root 28571 2011-01-12 08:32 ./firefox/utsgpb69.default/Cache/A3C05D45d01
-rw------- 1 root root 191060 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/98490367d01
-rw------- 1 root root 280218 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/C4B083EDd01
-rw------- 1 root root 32676 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/013DD5D3d01
-rw------- 1 root root 60952 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/2AF0941Fd01
-rw------- 1 root root 18844 2011-01-12 08:53 ./firefox/utsgpb69.default/Cache/20CB0181d01
-rw------- 1 root root 43416 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/6EB7D82Ed01
-rw------- 1 root root 36679 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/895C87C6d01
-rw------- 1 root root 31042 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/3EFB0982d01
-rw------- 1 root root 55699 2011-01-12 10:55 ./firefox/utsgpb69.default/Cache/4F6E7992d01
-rw------- 1 root root 29191 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/68F06A24d01
-rw------- 1 root root 145558 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/592E834Dd01
-rw------- 1 root root 271000 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/67D148DDd01
-rw------- 1 root root 30461 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/EDCF7E01d01
-rw------- 1 root root 85522 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/23F76F17d01
-rw------- 1 root root 19694 2011-01-12 07:18 ./firefox/utsgpb69.default/Cache/1C4743D3d01
-rw------- 1 root root 24678 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/7833D82Dd01
-rw------- 1 root root 32061 2011-01-12 08:35 ./firefox/utsgpb69.default/Cache/AFBE957Ed01
-rw------- 1 root root 54877 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/9F53A0F1d01
-rw------- 1 root root 19553 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/99F64200d01
-rw------- 1 root root 41172 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/2C375DD2d01
-rw------- 1 root root 222623 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/0F587E81d01
-rw------- 1 root root 20120 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/AD5D7812d01
-rw------- 1 root root 130097 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/6F5F4DFEd01
-rw------- 1 root root 27197 2011-01-12 08:50 ./firefox/utsgpb69.default/Cache/59A74190d01
-rw------- 1 root root 57276 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/47C73261d01
-rw------- 1 root root 101772 2011-01-12 08:51 ./firefox/utsgpb69.default/Cache/2D1526CBd01
-rw------- 1 root root 252947 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/3AD307ABd01
-rw------- 1 root root 119957 2011-01-12 10:39 ./firefox/utsgpb69.default/Cache/B23073D8d01
-rw------- 1 root root 25405 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/654F93DCd01
-rw------- 1 root root 32933 2011-01-12 07:12 ./firefox/utsgpb69.default/Cache/32B0EA89d01
-rw------- 1 root root 51220 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/1E39D46Dd01
-rw------- 1 root root 40236 2011-01-12 08:35 ./firefox/utsgpb69.default/Cache/898A447Ed01
-rw------- 1 root root 22664 2011-01-12 10:47 ./firefox/utsgpb69.default/Cache/3D1A6F8Fd01
-rw------- 1 root root 27313 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/8DDBF755d01
-rw------- 1 root root 23652 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/C4341D22d01
-rw------- 1 root root 20312 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/63923D8Bd01
-rw------- 1 root root 78146 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/98B6EA7Ad01
-rw------- 1 root root 18602 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/553C70D9d01
-rw------- 1 root root 172655 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/CCBE393Fd01
-rw------- 1 root root 97264 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/9F03F64Ed01
-rw------- 1 root root 32241 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/41A79BA4d01
-rw------- 1 root root 129906 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/A73AAFAFd01
-rw------- 1 root root 184103 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/FAA2AA85d01
-rw------- 1 root root 60244 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/D1C4D4F1d01
-rw------- 1 root root 83542 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/54D4D681d01
-rw------- 1 root root 87797 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/CD4913BDd01
-rw------- 1 root root 25888 2011-01-12 08:32 ./firefox/utsgpb69.default/Cache/D6042E29d01
-rw------- 1 root root 150079 2011-01-12 08:35 ./firefox/utsgpb69.default/Cache/A8A0A9BCd01
-rw------- 1 root root 197288 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/0D8F852Dd01
-rw------- 1 root root 149444 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/3450972Bd01
-rw------- 1 root root 21753 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/FA1E0B12d01
-rw------- 1 root root 19823 2011-01-12 08:56 ./firefox/utsgpb69.default/Cache/E9A5DE2Dd01
-rw------- 1 root root 170252 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/92F9C064d01
-rw------- 1 root root 232607 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/2C386EDCd01
-rw------- 1 root root 44809 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/AFF9A10Cd01
-rw------- 1 root root 166497 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/15CC7083d01
-rw------- 1 root root 37266 2011-01-12 07:32 ./firefox/utsgpb69.default/Cache/0EFF88C3d01
-rw------- 1 root root 24175 2011-01-12 08:15 ./firefox/utsgpb69.default/Cache/DF08CDC4d01
-rw------- 1 root root 24917 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/05DFB104d01
-rw------- 1 root root 54075 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/088849D2d01
-rw------- 1 root root 176323 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/27EDEBDCd01
-rw------- 1 root root 162866 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/34A43D38d01
-rw------- 1 root root 18973 2011-01-12 11:05 ./firefox/utsgpb69.default/Cache/1694BFFFd01
-rw------- 1 root root 27395 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/6A1CE479d01
-rw------- 1 root root 68566 2011-01-12 08:35 ./firefox/utsgpb69.default/Cache/DB072C03d01
-rw------- 1 root root 21704 2011-01-12 08:39 ./firefox/utsgpb69.default/Cache/DCF30E0Ad01
-rw------- 1 root root 39208 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/2BBA97A3d01
-rw------- 1 root root 24678 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/CE6E2E3Ad01
-rw------- 1 root root 52040 2011-01-12 13:11 ./firefox/utsgpb69.default/Cache/93898CACd01
-rw------- 1 root root 153875 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/F2D0AC81d01
-rw------- 1 root root 55774 2011-01-12 08:24 ./firefox/utsgpb69.default/Cache/79DBAAABd01
-rw------- 1 root root 55087 2011-01-12 13:14 ./firefox/utsgpb69.default/Cache/FE481DACd01
-rw------- 1 root root 27461 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/07773364d01
-rw------- 1 root root 46079 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/61310760d01
-rw------- 1 root root 20090 2011-01-12 08:32 ./firefox/utsgpb69.default/Cache/18927C8Cd01
-rw------- 1 root root 172195 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/FE01328Dd01
-rw------- 1 root root 19826 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/43F57918d01
-rw------- 1 root root 17305 2011-01-12 09:04 ./firefox/utsgpb69.default/Cache/BB29CB54d01
-rw------- 1 root root 47012 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/27DA232Fd01
-rw------- 1 root root 29448 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/CEEF1936d01
-rw------- 1 root root 109470 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/B9345882d01
-rw------- 1 root root 17629 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/B4A9AADDd01
-rw------- 1 root root 36055 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/D61D29ACd01
-rw------- 1 root root 241507 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/13640C69d01
-rw------- 1 root root 20316 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/AB31F1CAd01
-rw------- 1 root root 196341 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/4AFC87C3d01
-rw------- 1 root root 23542 2011-01-12 07:07 ./firefox/utsgpb69.default/Cache/E6BE7911d01
-rw------- 1 root root 64613 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/C8FBE89Ad01
-rw------- 1 root root 35540 2011-01-12 08:17 ./firefox/utsgpb69.default/Cache/220F95EEd01
-rw------- 1 root root 38002 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/D1DF5EB5d01
-rw------- 1 root root 23664 2011-01-12 08:17 ./firefox/utsgpb69.default/Cache/C9BC374Ed01
-rw------- 1 root root 64200 2011-01-12 10:41 ./firefox/utsgpb69.default/Cache/008C6605d01
-rw------- 1 root root 59034 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/07C36DD8d01
-rw------- 1 root root 27107 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/9E1E614Ed01
-rw------- 1 root root 91133 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/6A8CCB80d01
-rw------- 1 root root 156707 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/BA56CB21d01
-rw------- 1 root root 57254 2011-01-12 08:15 ./firefox/utsgpb69.default/Cache/DD55C2DFd01
-rw------- 1 root root 104275 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/F56CFBF0d01
-rw------- 1 root root 157532 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/9F499191d01
-rw------- 1 root root 178213 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/BCB724AAd01
-rw------- 1 root root 37749 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/F9AB0422d01
-rw------- 1 root root 27441 2011-01-12 08:15 ./firefox/utsgpb69.default/Cache/91B63165d01
-rw------- 1 root root 30624 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/84A9CA9Fd01
-rw------- 1 root root 163131 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/73EC61D4d01
-rw------- 1 root root 225729 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/389A1098d01
-rw------- 1 root root 49085 2011-01-12 08:51 ./firefox/utsgpb69.default/Cache/A38224C0d01
-rw------- 1 root root 22889 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/15B70554d01
-rw------- 1 root root 53143 2011-01-12 10:43 ./firefox/utsgpb69.default/Cache/627FBF74d01
-rw------- 1 root root 301079 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/978E6B48d01
-rw------- 1 root root 249444 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/8CB693A7d01
-rw------- 1 root root 162987 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/E9C55D7Ad01
-rw------- 1 root root 139977 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/1D89ED92d01
-rw------- 1 root root 43508 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/0873E4D5d01
-rw------- 1 root root 871374 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/4FDAC4BAd01
-rw------- 1 root root 68584 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/C59FE7ACd01
-rw------- 1 root root 17454 2011-01-12 08:53 ./firefox/utsgpb69.default/Cache/60DCF185d01
-rw------- 1 root root 5894748 2011-01-12 13:14 ./firefox/utsgpb69.default/Cache/_CACHE_003_
-rw------- 1 root root 16720 2011-01-12 08:53 ./firefox/utsgpb69.default/Cache/6F32C5CFd01
-rw------- 1 root root 19820 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/89228A9Dd01
-rw------- 1 root root 1106527 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/D266BF58d01
-rw------- 1 root root 50247 2011-01-12 08:51 ./firefox/utsgpb69.default/Cache/EFADB720d01
-rw------- 1 root root 49667 2011-01-12 08:17 ./firefox/utsgpb69.default/Cache/E9C5D536d01
-rw------- 1 root root 412135 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/1A5B83E2d01
-rw------- 1 root root 31248 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/3E0DE3B5d01
-rw------- 1 root root 174889 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/8B009BE0d01
-rw------- 1 root root 170741 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/4380D42Bd01
-rw------- 1 root root 17322 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/9C11657Ed01
-rw------- 1 root root 43057 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/D75CE696d01
-rw------- 1 root root 95550 2011-01-12 13:14 ./firefox/utsgpb69.default/Cache/EF99A6B1d01
-rw------- 1 root root 33322 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/CD79396Fd01
-rw------- 1 root root 21219 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/4F80A4ABd01
-rw------- 1 root root 36654 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/3D481E14d01
-rw------- 1 root root 46046 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/55E2AAF9d01
-rw------- 1 root root 133774 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/82F8ED18d01
-rw------- 1 root root 27197 2011-01-12 08:47 ./firefox/utsgpb69.default/Cache/7AA8DF7Fd01
-rw------- 1 root root 29416 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/CB420BD2d01
-rw------- 1 root root 29581 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/8EA64124d01
-rw------- 1 root root 197243 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/AFB35F92d01
-rw------- 1 root root 19820 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/47A80D4Fd01
-rw------- 1 root root 48839 2011-01-12 08:39 ./firefox/utsgpb69.default/Cache/B3C577D1d01
-rw------- 1 root root 20431 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/770A8FA0d01
-rw------- 1 root root 36690 2011-01-12 08:39 ./firefox/utsgpb69.default/Cache/F3FDFFAFd01
-rw------- 1 root root 46336 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/BCB055A7d01
-rw------- 1 root root 31358 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/9DF443F4d01
-rw------- 1 root root 18421 2011-01-12 07:06 ./firefox/utsgpb69.default/Cache/80B036F4d01
-rw------- 1 root root 36078 2011-01-12 08:39 ./firefox/utsgpb69.default/Cache/91ADBA10d01
-rw------- 1 root root 20685 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/D3BCF2B4d01
-rw------- 1 root root 216010 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/C8A194AFd01
-rw------- 1 root root 30782 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/A3AD93AFd01
-rw------- 1 root root 232739 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/99D4292Dd01
-rw------- 1 root root 38625 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/A9393A13d01
-rw------- 1 root root 57812 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/AEEAABC2d01
-rw------- 1 root root 391575 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/FABD44A1d01
-rw------- 1 root root 83997 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/4FE07ECEd01
-rw------- 1 root root 34760 2011-01-12 08:15 ./firefox/utsgpb69.default/Cache/2B7F7DF3d01
-rw------- 1 root root 36871 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/895DFCA2d01
-rw------- 1 root root 197992 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/5DF612BEd01
-rw------- 1 root root 65812 2011-01-12 13:10 ./firefox/utsgpb69.default/Cache/_CACHE_MAP_
-rw------- 1 root root 48907 2011-01-12 08:51 ./firefox/utsgpb69.default/Cache/A5F9CEA7d01
-rw------- 1 root root 93325 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/EFDDCFCEd01
-rw------- 1 root root 164529 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/1DC86041d01
-rw------- 1 root root 45042 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/DB893D97d01
-rw------- 1 root root 35540 2011-01-12 08:18 ./firefox/utsgpb69.default/Cache/C0282B1Dd01
-rw------- 1 root root 16669 2011-01-12 11:05 ./firefox/utsgpb69.default/Cache/6FDDB4D2d01
-rw------- 1 root root 147966 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/960CBC66d01
-rw------- 1 root root 41717 2011-01-12 08:55 ./firefox/utsgpb69.default/Cache/251D1D43d01
-rw------- 1 root root 55948 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/D88B8212d01
-rw------- 1 root root 38106 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/9DC41B20d01
-rw------- 1 root root 33231 2011-01-12 08:39 ./firefox/utsgpb69.default/Cache/64DCB567d01
-rw------- 1 root root 36225 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/A2F273D4d01
-rw------- 1 root root 21101 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/51727FB8d01
-rw------- 1 root root 74101 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/9D2C41DDd01
-rw------- 1 root root 22101 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/D8CC7647d01
-rw------- 1 root root 25583 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/B34D9275d01
-rw------- 1 root root 2249219 2011-01-12 13:14 ./firefox/utsgpb69.default/Cache/_CACHE_001_
-rw------- 1 root root 18665 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/09F83EA9d01
-rw------- 1 root root 24523 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/14926420d01
-rw------- 1 root root 27540 2011-01-12 10:38 ./firefox/utsgpb69.default/Cache/A7531EE3d01
-rw------- 1 root root 18994 2011-01-12 09:02 ./firefox/utsgpb69.default/Cache/60AA04C3d01
-rw------- 1 root root 106697 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/D0FD447Cd01
-rw------- 1 root root 18371 2011-01-12 08:53 ./firefox/utsgpb69.default/Cache/C75ADE41d01
-rw------- 1 root root 34803 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/7ED1FA02d01
-rw------- 1 root root 30904 2011-01-12 08:53 ./firefox/utsgpb69.default/Cache/308EC962d01
-rw------- 1 root root 174097 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/22AC22E2d01
-rw------- 1 root root 264521 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/18C61CFEd01
-rw------- 1 root root 18405 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/1C7AFF14d01
-rw------- 1 root root 26379 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/F5305D8Cd01
-rw------- 1 root root 187592 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/BEC05087d01
-rw------- 1 root root 35436 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/0BDB69DBd01
-rw------- 1 root root 58787 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/2C23EB09d01
-rw------- 1 root root 16702 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/6C4C3CE5d01
-rw------- 1 root root 18974 2011-01-12 10:23 ./firefox/utsgpb69.default/Cache/451676CEd01
-rw------- 1 root root 146686 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/221C0141d01
-rw------- 1 root root 144514 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/630BB68Fd01
-rw------- 1 root root 24618 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/01807E19d01
-rw------- 1 root root 56186 2011-01-12 10:38 ./firefox/utsgpb69.default/Cache/94862D8Ed01
-rw------- 1 root root 58941 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/508C9BDBd01
-rw------- 1 root root 20794 2011-01-12 08:15 ./firefox/utsgpb69.default/Cache/067CA9AAd01
-rw------- 1 root root 19820 2011-01-12 08:32 ./firefox/utsgpb69.default/Cache/E7A0B46Ed01
-rw------- 1 root root 143157 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/F279FBD2d01
-rw------- 1 root root 143382 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/AD921404d01
-rw------- 1 root root 166821 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/8D37DE9Ad01
-rw------- 1 root root 45545 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/1D7241F9d01
-rw------- 1 root root 73521 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/DFD1E425d01
-rw------- 1 root root 136004 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/CFD822CDd01
-rw------- 1 root root 225271 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/DFC513B8d01
-rw------- 1 root root 20399 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/9175F601d01
-rw------- 1 root root 24972 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/290C8768d01
-rw------- 1 root root 140905 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/043D65B8d01
-rw------- 1 root root 186231 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/101C1691d01
-rw------- 1 root root 148576 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/9BF3C979d01
-rw------- 1 root root 53058 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/F2B016D3d01
-rw------- 1 root root 21971 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/3D8CC51Ed01
-rw------- 1 root root 2417818 2011-01-12 13:14 ./firefox/utsgpb69.default/Cache/_CACHE_002_
-rw------- 1 root root 33533 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/4AF28467d01
-rw------- 1 root root 39273 2011-01-12 08:28 ./firefox/utsgpb69.default/Cache/32F5D980d01
-rw------- 1 root root 51808 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/92D08D6Cd01
-rw------- 1 root root 132665 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/1A6710A9d01
-rw------- 1 root root 21356 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/C09F71A1d01
-rw------- 1 root root 232343 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/FA7E6961d01
-rw------- 1 root root 17300 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/B140CF3Ed01
-rw------- 1 root root 30781 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/714D1B5Fd01
-rw------- 1 root root 18272 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/AB18B4C2d01
-rw------- 1 root root 17625 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/D4002D0Fd01
-rw------- 1 root root 25070 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/13506449d01
-rw------- 1 root root 89444 2011-01-12 13:10 ./firefox/utsgpb69.default/Cache/B3439DCCd01
-rw------- 1 root root 70113 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/6A48A5C2d01
-rw------- 1 root root 29952 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/9BB9E28Ad01
-rw------- 1 root root 57369 2011-01-12 08:32 ./firefox/utsgpb69.default/Cache/6B795FDCd01
-rw------- 1 root root 21798 2011-01-12 08:23 ./firefox/utsgpb69.default/Cache/51732E99d01
-rw------- 1 root root 28391 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/87951EFFd01
-rw------- 1 root root 45246 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/3FBD295Ed01
-rw------- 1 root root 133208 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/45DA5E5Dd01
-rw------- 1 root root 84274 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/02B20AAAd01
-rw------- 1 root root 19823 2011-01-12 08:51 ./firefox/utsgpb69.default/Cache/3F4BF8D6d01
-rw------- 1 root root 135719 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/D9F0FFDDd01
-rw------- 1 root root 22933 2011-01-12 08:32 ./firefox/utsgpb69.default/Cache/4816696Fd01
-rw------- 1 root root 18534 2011-01-12 08:46 ./firefox/utsgpb69.default/Cache/0C14F1ECd01
-rw------- 1 root root 20262 2011-01-12 08:31 ./firefox/utsgpb69.default/Cache/13C9BB89d01
-rw------- 1 root root 275283 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/F0D0EA12d01
-rw------- 1 root root 36250 2011-01-12 08:32 ./firefox/utsgpb69.default/Cache/3DDC2431d01
-rw------- 1 root root 22901 2011-01-12 08:34 ./firefox/utsgpb69.default/Cache/EEB92B0Fd01
-rw------- 1 root root 216479 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/6FA60853d01
-rw------- 1 root root 21397 2011-01-12 08:53 ./firefox/utsgpb69.default/Cache/364C1B2Bd01
-rw------- 1 root root 142070 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/2DB11179d01
-rw------- 1 root root 160251 2011-01-12 08:45 ./firefox/utsgpb69.default/Cache/0CB79FF3d01
-rw------- 1 root root 25359 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/A02AB491d01
-rw------- 1 root root 18378 2011-01-12 08:32 ./firefox/utsgpb69.default/Cache/352CFB54d01
-rw------- 1 root root 127997 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/71B33273d01
-rw------- 1 root root 159577 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/B9D8BF92d01
-rw------- 1 root root 42333 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/69104025d01
-rw------- 1 root root 258026 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/36C10716d01
-rw------- 1 root root 26027 2011-01-12 13:14 ./firefox/utsgpb69.default/Cache/354CCC4Cd01
-rw------- 1 root root 63941 2011-01-12 08:18 ./firefox/utsgpb69.default/Cache/3F9FABC6d01
-rw------- 1 root root 18602 2011-01-12 08:37 ./firefox/utsgpb69.default/Cache/23039592d01
-rw------- 1 root root 169541 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/4050E26Ed01
-rw------- 1 root root 20559 2011-01-12 08:35 ./firefox/utsgpb69.default/Cache/438F9D80d01
-rw------- 1 root root 29569 2011-01-12 08:51 ./firefox/utsgpb69.default/Cache/1ED16F06d01
-rw------- 1 root root 47267 2011-01-12 10:22 ./firefox/utsgpb69.default/Cache/D3573611d01
-rw------- 1 root root 141977 2011-01-12 08:16 ./firefox/utsgpb69.default/Cache/5EF8E5A9d01
-rw------- 1 root root 151390 2011-01-12 08:52 ./firefox/utsgpb69.default/Cache/E7943D8Cd01
lrwxrwxrwx 1 root root 18 2011-01-12 13:10 ./firefox/utsgpb69.default/lock -> 192.168.2.3:+11124
-rw------- 1 root root 70558 2011-01-12 13:14 ./firefox/utsgpb69.default/sessionstore.js
-rw-r--r-- 1 root root 150275 2011-01-01 11:13 ./firefox/utsgpb69.default/compreg.dat
-rw-r--r-- 1 root root 0 2011-01-12 13:15 ./firefox/utsgpb69.default/places.sqlite-journal
-rw-r--r-- 1 root root 3608 2011-01-12 13:14 ./firefox/utsgpb69.default/cookies.sqlite-journal
-rw-r--r-- 1 root root 3115 2011-01-01 11:13 ./firefox/utsgpb69.default/extensions.rdf
-rw-r--r-- 1 root root 1363161 2011-01-06 09:21 ./firefox/utsgpb69.default/XUL.mfasl
-rw-r--r-- 1 root root 300 2011-01-01 11:13 ./firefox/utsgpb69.default/extensions.ini
-rw-r--r-- 1 root root 17403 2011-01-12 11:17 ./firefox/utsgpb69.default/prefs.js
-rw------- 1 root root 68994 2011-01-12 13:10 ./firefox/utsgpb69.default/sessionstore.bak
-rw-r--r-- 1 root root 2262184 2010-12-31 18:35 ./firefox/utsgpb69.default/XPC.mfasl
-rw-r--r-- 1 root root 100711 2011-01-01 11:13 ./firefox/utsgpb69.default/xpti.dat
-rw------- 1 root root 21884 2011-01-08 08:38 ./firefox/utsgpb69.default/bookmarkbackups/bookmarks-2011-01-08.json
-rw------- 1 root root 22331 2011-01-10 09:51 ./firefox/utsgpb69.default/bookmarkbackups/bookmarks-2011-01-10.json
-rw------- 1 root root 22331 2011-01-12 11:17 ./firefox/utsgpb69.default/bookmarkbackups/bookmarks-2011-01-12.json
-rw------- 1 root root 22331 2011-01-11 10:55 ./firefox/utsgpb69.default/bookmarkbackups/bookmarks-2011-01-11.json
-rw------- 1 root root 21884 2011-01-07 08:21 ./firefox/utsgpb69.default/bookmarkbackups/bookmarks-2011-01-07.json
-rw------- 1 root root 21884 2011-01-09 09:07 ./firefox/utsgpb69.default/bookmarkbackups/bookmarks-2011-01-09.json
-rw-r--r-- 1 root root 4496 2011-01-11 17:37 ./firefox/utsgpb69.default/blocklist.xml
-rw-r--r-- 1 root root 280 2011-01-01 11:13 ./firefox/utsgpb69.default/extensions.cache

```

---

### Post by uRock on 2011-01-12
Files in the crash folder should not be listed as root either, but maybe they are listed as root because the installs/updates were ran as root. I am not sure about this. Here is the list of folder permissions in that directory on my system. ```
rabbit@ronnie-desktop:~$ cd ~/.mozilla/firefox/Crash\ Reports
rabbit@ronnie-desktop:~/.mozilla/firefox/Crash Reports$ ls -ail
total 56
2884188 drwxr-xr-x 3 rabbit rabbit 4096 2010-12-10 09:36 .
2883751 drwxr-xr-x 5 rabbit rabbit 4096 2009-12-23 14:00 ..
2886970 -rw-r--r-- 1 rabbit rabbit   55 2010-11-01 11:34 crashreporter.ini
2884189 -rw-r--r-- 1 rabbit rabbit   10 2009-11-08 12:17 InstallTime20091029152254
2884190 -rw-r--r-- 1 rabbit rabbit   10 2009-11-08 12:00 InstallTime20091102141836
2886817 -rw------- 1 rabbit rabbit   10 2010-09-10 07:30 InstallTime20100825164301
2883659 -rw------- 1 rabbit rabbit   10 2010-09-17 07:42 InstallTime20100915180533
2892970 -rw------- 1 rabbit rabbit   10 2010-12-09 09:44 InstallTime20100922075949
2887034 -rw------- 1 rabbit rabbit   10 2010-10-21 07:17 InstallTime20101013121314
2884154 -rw------- 1 rabbit rabbit   10 2010-10-28 07:05 InstallTime20101027124711
2892571 -rw------- 1 rabbit rabbit   10 2010-12-09 10:00 InstallTime20101027124735
2883730 -rw------- 1 rabbit rabbit   10 2010-12-10 09:36 InstallTime20101206121716
2886825 -rw------- 1 rabbit rabbit   10 2010-11-01 11:34 LastCrash
5900491 drwxr-xr-x 2 rabbit rabbit 4096 2010-11-01 11:34 pending
2886931 -rw-r--r-- 1 rabbit rabbit    0 2010-11-01 11:34 submit.log

```

---

### Post by bilkay on 2011-01-12
I changed ownership of everything to my username and everything seems OK. I'll keep an eye on this to see if it ever happens again.

---

### Post by bilkay on 2011-01-12
Update: After changing all ownerships to my username, after running firefox, I'm finding new files owned by root! The only caveat I can think of is that the .mozilla directory is autofs mounted using ssh.

/etc/auto.master
```

/userdirs       /etc/auto.ssh  -v --ghost --timeout=10

```

/etc/auto.ssh
```

myusername.mozilla -fstype=fuse,port=12023,rw,nodev,nonempty,noatime,allow_other,max_read=65536 :sshfs\#Saturn:\/home/myusername/.mozilla

```

I checked the executables for suid and found none.

---

### Post by WinstonChurchill on 2011-01-15
Run firefox, and then post the output of the command: 'ps axu | grep firefox'

I get:
```

DesktopUser@DesktopBox:~$** ps axu | grep firefox**
DesktopUser  2433  0.0  0.0   4148   576 ?        S    08:36   0:00 /bin/sh /usr/lib/firefox-3.6.13/firefox
DesktopUser  2437  0.0  0.0   4148   576 ?        S    08:36   0:00 /bin/sh /usr/lib/firefox-3.6.13/run-mozilla.sh /usr/lib/firefox-3.6.13/firefox-bin
DesktopUser  2441  1.1  5.2 752124 213344 ?       Sl   08:36   3:30 /usr/lib/firefox-3.6.13/firefox-bin
DesktopUser  5153  0.0  0.0   8952   852 pts/3    S+   13:43   0:00 grep --color=auto firefox

```Also, I can confirm that Firefox should not be creating any files owned by root:
```

DesktopUser@DesktopBox:~/.mozilla$ ls -R -l
.:
total 8
drwx------ 3 DesktopUser DesktopUser 4096 2010-08-11 21:11 extensions
drwx------ 4 DesktopUser DesktopUser 4096 2010-09-10 11:03 firefox

./extensions:
total 4
drwxr-xr-x 2 DesktopUser DesktopUser 4096 2010-08-11 21:11 {ec8030f7-c20a-464f-9b0e-13a3a9e97384}

./extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}:
total 0

./firefox:
total 12
drwx------ 9 DesktopUser DesktopUser 4096 2011-01-15 13:38 bc3huk63.default
drwx------ 3 DesktopUser DesktopUser 4096 2010-12-09 20:42 Crash Reports
-rw-r--r-- 1 DesktopUser DesktopUser   94 2010-08-11 21:11 profiles.ini

./firefox/bc3huk63.default:
total 66452
drwxr-xr-x 2 DesktopUser DesktopUser     4096 2011-01-15 12:42 adblockplus
-rw-r--r-- 1 DesktopUser DesktopUser     4496 2011-01-14 20:47 blocklist.xml
drwx------ 2 DesktopUser DesktopUser     4096 2011-01-14 23:44 bookmarkbackups
-rw-r--r-- 1 DesktopUser DesktopUser    20162 2010-08-11 21:11 bookmarks.html
drwxr-xr-x 2 DesktopUser DesktopUser    12288 2011-01-15 13:37 Cache
-rw------- 1 DesktopUser DesktopUser   131072 2011-01-15 09:27 cert8.db
-rw------- 1 DesktopUser DesktopUser     1133 2011-01-04 00:09 cert_override.txt
drwxr-xr-x 2 DesktopUser DesktopUser     4096 2010-08-11 21:11 chrome
-rw------- 1 DesktopUser DesktopUser      168 2010-12-09 20:42 compatibility.ini
-rw-r--r-- 1 DesktopUser DesktopUser   150876 2010-12-30 10:54 compreg.dat
-rw-r--r-- 1 DesktopUser DesktopUser     7168 2011-01-15 08:38 content-prefs.sqlite
-rw-r--r-- 1 DesktopUser DesktopUser   207872 2011-01-15 13:38 cookies.sqlite
-rw-r--r-- 1 DesktopUser DesktopUser    84104 2011-01-15 13:38 cookies.sqlite-journal
-rw-r--r-- 1 DesktopUser DesktopUser    82944 2011-01-15 08:38 downloads.sqlite
drwxr-xr-x 4 DesktopUser DesktopUser     4096 2011-01-14 20:47 extensions
-rw-r--r-- 1 DesktopUser DesktopUser      800 2010-12-30 10:54 extensions.cache
-rw-r--r-- 1 DesktopUser DesktopUser      774 2010-12-30 10:54 extensions.ini
-rw-r--r-- 1 DesktopUser DesktopUser    26468 2011-01-09 00:18 extensions.rdf
-rw-r--r-- 1 DesktopUser DesktopUser    64512 2011-01-15 13:27 formhistory.sqlite
-rw------- 1 DesktopUser DesktopUser    16384 2011-01-14 23:44 key3.db
-rw-r--r-- 1 DesktopUser DesktopUser    13878 2011-01-15 08:38 localstore.rdf
lrwxrwxrwx 1 DesktopUser DesktopUser       15 2011-01-15 08:36 lock -> 127.0.1.1:+2441
-rw-r--r-- 1 DesktopUser DesktopUser    11956 2011-01-04 23:34 mimeTypes.rdf
drwx------ 2 DesktopUser DesktopUser     4096 2010-09-26 21:41 minidumps
drwx------ 2 DesktopUser DesktopUser     4096 2010-12-17 00:07 OfflineCache
-rw-r--r-- 1 DesktopUser DesktopUser     2048 2011-01-15 08:38 permissions.sqlite
-rw-r--r-- 1 DesktopUser DesktopUser        7 2010-11-09 01:29 persdict.dat
-rw-r--r-- 1 DesktopUser DesktopUser 10924032 2011-01-15 13:37 places.sqlite
-rw-r--r-- 1 DesktopUser DesktopUser        0 2011-01-15 13:37 places.sqlite-journal
-rw------- 1 DesktopUser DesktopUser     3179 2010-11-18 22:58 pluginreg.dat
-rw-r--r-- 1 DesktopUser DesktopUser    34959 2011-01-15 08:38 prefs.js
-rw-r--r-- 1 DesktopUser DesktopUser    14565 2011-01-15 08:36 search.json
-rw-r--r-- 1 DesktopUser DesktopUser     2048 2010-08-11 21:11 search.sqlite
-rw------- 1 DesktopUser DesktopUser    16384 2010-08-11 21:11 secmod.db
-rw------- 1 DesktopUser DesktopUser   216020 2010-08-31 16:42 sessionstore-1.js
-rw------- 1 DesktopUser DesktopUser    36615 2010-10-02 18:36 sessionstore-2.js
-rw------- 1 DesktopUser DesktopUser    69493 2010-12-16 20:48 sessionstore-3.js
-rw------- 1 DesktopUser DesktopUser   116033 2010-12-31 20:13 sessionstore-4.js
-rw------- 1 DesktopUser DesktopUser   106885 2011-01-15 13:38 sessionstore.js
-rw-r--r-- 1 DesktopUser DesktopUser    14336 2011-01-15 08:38 signons.sqlite
-rw-r--r-- 1 DesktopUser DesktopUser 51081216 2011-01-15 13:11 urlclassifier3.sqlite
-rw-r--r-- 1 DesktopUser DesktopUser      154 2011-01-15 08:40 urlclassifierkey3.txt
-rw-r--r-- 1 DesktopUser DesktopUser   292864 2011-01-15 08:38 webappsstore.sqlite
-rw-r--r-- 1 DesktopUser DesktopUser  2545663 2010-12-31 14:43 XPC.mfasl
-rw-r--r-- 1 DesktopUser DesktopUser   100823 2010-12-30 10:54 xpti.dat
-rw-r--r-- 1 DesktopUser DesktopUser  1517938 2011-01-15 08:38 XUL.mfasl

./firefox/bc3huk63.default/adblockplus:
total 1740
-rw-r--r-- 1 DesktopUser DesktopUser 298179 2011-01-14 20:43 patterns-backup1.ini
-rw-r--r-- 1 DesktopUser DesktopUser 298179 2011-01-13 16:07 patterns-backup2.ini
-rw-r--r-- 1 DesktopUser DesktopUser 298178 2011-01-12 22:52 patterns-backup3.ini
-rw-r--r-- 1 DesktopUser DesktopUser 298176 2011-01-11 22:55 patterns-backup4.ini
-rw-r--r-- 1 DesktopUser DesktopUser 297475 2011-01-10 23:30 patterns-backup5.ini
-rw-r--r-- 1 DesktopUser DesktopUser 285266 2011-01-15 12:42 patterns.ini

./firefox/bc3huk63.default/bookmarkbackups:
total 48
-rw------- 1 DesktopUser DesktopUser 5570 2011-01-05 14:24 bookmarks-2011-01-05.json
-rw------- 1 DesktopUser DesktopUser 5570 2011-01-09 00:55 bookmarks-2011-01-09.json
-rw------- 1 DesktopUser DesktopUser 5570 2011-01-11 00:16 bookmarks-2011-01-11.json
-rw------- 1 DesktopUser DesktopUser 5570 2011-01-12 02:18 bookmarks-2011-01-12.json
-rw------- 1 DesktopUser DesktopUser 5570 2011-01-13 15:42 bookmarks-2011-01-13.json
-rw------- 1 DesktopUser DesktopUser 5658 2011-01-14 23:44 bookmarks-2011-01-14.json

./firefox/bc3huk63.default/Cache:
total 24500
-rw------- 1 DesktopUser DesktopUser   20768 2011-01-15 13:25 003A2119d01
-rw------- 1 DesktopUser DesktopUser   21067 2011-01-15 13:25 0089868Bd01
-rw------- 1 DesktopUser DesktopUser   37708 2011-01-15 13:35 008C6605d01
-rw------- 1 DesktopUser DesktopUser   22589 2011-01-15 13:25 00D4A16Ad01
-rw------- 1 DesktopUser DesktopUser   67104 2011-01-15 13:18 0358E9E9d01
-rw------- 1 DesktopUser DesktopUser   22120 2011-01-15 13:25 036CD032d01
-rw------- 1 DesktopUser DesktopUser   27285 2011-01-15 13:25 044C52F6d01
-rw------- 1 DesktopUser DesktopUser   62545 2011-01-15 13:16 0636B572d01
-rw------- 1 DesktopUser DesktopUser   56826 2011-01-15 13:19 06CBDBAFd01
-rw------- 1 DesktopUser DesktopUser   22091 2011-01-15 13:25 06FA98BEd01
-rw------- 1 DesktopUser DesktopUser   16633 2011-01-15 13:17 079C1D5Ad01
-rw------- 1 DesktopUser DesktopUser   24707 2011-01-15 09:27 07B2C63Ed01
-rw------- 1 DesktopUser DesktopUser   22689 2011-01-15 08:49 0A138D66d01
-rw------- 1 DesktopUser DesktopUser   47112 2011-01-15 13:16 0AB09204d01
-rw------- 1 DesktopUser DesktopUser   23934 2011-01-15 13:25 0B294605d01
-rw------- 1 DesktopUser DesktopUser   25414 2011-01-15 09:27 0CC0A352d01
-rw------- 1 DesktopUser DesktopUser   21560 2011-01-15 13:24 0D860418d01
-rw------- 1 DesktopUser DesktopUser   42738 2011-01-15 13:25 0DBFA11Ed01
-rw------- 1 DesktopUser DesktopUser   16807 2011-01-15 13:15 0E84ACFBd01
-rw------- 1 DesktopUser DesktopUser   61450 2011-01-15 13:25 0FA6AB8Fd01
-rw------- 1 DesktopUser DesktopUser   22903 2011-01-15 13:17 1028BCC1d01
-rw------- 1 DesktopUser DesktopUser   18329 2011-01-15 13:19 11360347d01
-rw------- 1 DesktopUser DesktopUser   44324 2011-01-15 09:41 116972E3d01
-rw------- 1 DesktopUser DesktopUser   24354 2011-01-15 13:25 141E4789d01
-rw------- 1 DesktopUser DesktopUser   17745 2011-01-15 13:25 141F7BA9d01
-rw------- 1 DesktopUser DesktopUser   38291 2011-01-15 13:13 15507A27d01
-rw------- 1 DesktopUser DesktopUser   25942 2011-01-15 13:25 15E7E293d01
-rw------- 1 DesktopUser DesktopUser   16425 2011-01-15 13:28 176A8BE5d01
-rw------- 1 DesktopUser DesktopUser   22615 2011-01-15 13:25 182AABF7d01
-rw------- 1 DesktopUser DesktopUser   20128 2011-01-15 13:25 189ACC1Bd01
-rw------- 1 DesktopUser DesktopUser   99432 2011-01-15 13:16 18A6357Cd01
-rw------- 1 DesktopUser DesktopUser   47966 2011-01-15 13:20 18AB127Fd01
-rw------- 1 DesktopUser DesktopUser   21729 2011-01-15 13:25 191EF232d01
-rw------- 1 DesktopUser DesktopUser   78327 2011-01-15 13:18 1937894Cd01
-rw------- 1 DesktopUser DesktopUser   17924 2011-01-15 13:25 1ADC5365d01
-rw------- 1 DesktopUser DesktopUser   23841 2011-01-15 13:19 1BD3F9DBd01
-rw------- 1 DesktopUser DesktopUser   20367 2011-01-15 13:24 1BE1946Cd01
-rw------- 1 DesktopUser DesktopUser   18180 2011-01-15 13:17 1DCBE2E9d01
-rw------- 1 DesktopUser DesktopUser   18092 2011-01-15 13:25 1EEC6FB0d01
-rw------- 1 DesktopUser DesktopUser   21023 2011-01-15 13:24 1F1062B2d01
-rw------- 1 DesktopUser DesktopUser   22064 2011-01-15 13:24 20442686d01
-rw------- 1 DesktopUser DesktopUser   21441 2011-01-15 13:25 20F59014d01
-rw------- 1 DesktopUser DesktopUser   20714 2011-01-15 13:25 214E70BFd01
-rw------- 1 DesktopUser DesktopUser   19222 2011-01-15 13:25 21BECB8Ed01
-rw------- 1 DesktopUser DesktopUser   30500 2011-01-15 09:19 2227E43Ed01
-rw------- 1 DesktopUser DesktopUser   23178 2011-01-15 13:25 224F8890d01
-rw------- 1 DesktopUser DesktopUser   26525 2011-01-15 13:19 22606378d01
-rw------- 1 DesktopUser DesktopUser   52868 2011-01-15 13:25 226CDF57d01
-rw------- 1 DesktopUser DesktopUser   20621 2011-01-15 13:25 231806D3d01
-rw------- 1 DesktopUser DesktopUser   51105 2011-01-15 13:20 2339967Bd01
-rw------- 1 DesktopUser DesktopUser   49363 2011-01-15 13:25 23C55E64d01
-rw------- 1 DesktopUser DesktopUser   20748 2011-01-15 13:25 24050908d01
-rw------- 1 DesktopUser DesktopUser   67258 2011-01-15 13:19 24C4A355d01
-rw------- 1 DesktopUser DesktopUser   43722 2011-01-15 13:20 24FAA855d01
-rw------- 1 DesktopUser DesktopUser   73960 2011-01-15 13:18 25A9D175d01
-rw------- 1 DesktopUser DesktopUser   19558 2011-01-15 13:17 2619BC2Ed01
-rw------- 1 DesktopUser DesktopUser   23702 2011-01-15 13:17 2659BA05d01
-rw------- 1 DesktopUser DesktopUser   57839 2011-01-15 13:25 27B6D480d01
-rw------- 1 DesktopUser DesktopUser   22803 2011-01-15 13:25 27DE5BDCd01
-rw------- 1 DesktopUser DesktopUser   25504 2011-01-15 13:19 2A48E2F8d01
-rw------- 1 DesktopUser DesktopUser   23684 2011-01-15 09:27 2A661391d01
-rw------- 1 DesktopUser DesktopUser   22931 2011-01-15 13:17 2AC08176d01
-rw------- 1 DesktopUser DesktopUser  105708 2011-01-15 13:24 2BA162E8d01
-rw------- 1 DesktopUser DesktopUser   22605 2011-01-15 13:25 2CC1B7B4d01
-rw------- 1 DesktopUser DesktopUser   54145 2011-01-15 09:27 2CE0294Ad01
-rw------- 1 DesktopUser DesktopUser   19334 2011-01-15 09:39 2CE8D446d01
-rw------- 1 DesktopUser DesktopUser   23267 2011-01-15 13:25 2ED8856Ed01
-rw------- 1 DesktopUser DesktopUser   16456 2011-01-15 13:17 2F05B02Ad01
-rw------- 1 DesktopUser DesktopUser   22700 2011-01-15 13:25 2F9A59D6d01
-rw------- 1 DesktopUser DesktopUser   23548 2011-01-15 13:25 301F490Ed01
-rw------- 1 DesktopUser DesktopUser   22337 2011-01-15 13:25 3069340Cd01
-rw------- 1 DesktopUser DesktopUser   40083 2011-01-15 13:19 3083EF2Fd01
-rw------- 1 DesktopUser DesktopUser  107251 2011-01-15 13:09 3088B62Fd01
-rw------- 1 DesktopUser DesktopUser   46252 2011-01-15 13:25 32D59684d01
-rw------- 1 DesktopUser DesktopUser   52314 2011-01-15 13:20 34FED6BBd01
-rw------- 1 DesktopUser DesktopUser   26027 2011-01-15 13:37 354CCC4Cd01
-rw------- 1 DesktopUser DesktopUser  115117 2011-01-15 13:35 359AE592d01
-rw------- 1 DesktopUser DesktopUser   16921 2011-01-15 13:28 3735DF17d01
-rw------- 1 DesktopUser DesktopUser   22944 2011-01-15 13:25 37ED0BE0d01
-rw------- 1 DesktopUser DesktopUser   20136 2011-01-15 13:17 39427671d01
-rw------- 1 DesktopUser DesktopUser  103756 2011-01-15 09:04 3997108Ed01
-rw------- 1 DesktopUser DesktopUser   33619 2011-01-15 13:19 3C1A40C4d01
-rw------- 1 DesktopUser DesktopUser   23129 2011-01-15 13:25 3C4FB3F9d01
-rw------- 1 DesktopUser DesktopUser   20166 2011-01-15 13:25 3CB1513Bd01
-rw------- 1 DesktopUser DesktopUser   62544 2011-01-15 09:41 3D0D60C3d01
-rw------- 1 DesktopUser DesktopUser   17432 2011-01-15 13:15 3D9EF80Dd01
-rw------- 1 DesktopUser DesktopUser   17672 2011-01-15 13:25 3DCB3279d01
-rw------- 1 DesktopUser DesktopUser   21231 2011-01-15 13:24 3DF0D377d01
-rw------- 1 DesktopUser DesktopUser   35325 2011-01-15 13:19 3E0F69ABd01
-rw------- 1 DesktopUser DesktopUser   35206 2011-01-15 09:41 3EF5D178d01
-rw------- 1 DesktopUser DesktopUser   25482 2011-01-15 13:25 3F291EC1d01
-rw------- 1 DesktopUser DesktopUser   18314 2011-01-15 13:19 4010C90Ad01
-rw------- 1 DesktopUser DesktopUser   20442 2011-01-15 13:25 4044CA4Fd01
-rw------- 1 DesktopUser DesktopUser   21963 2011-01-15 13:24 41BAD6DAd01
-rw------- 1 DesktopUser DesktopUser   21648 2011-01-15 13:24 41F8F7C6d01
-rw------- 1 DesktopUser DesktopUser   21920 2011-01-15 13:24 420D0FA2d01
-rw------- 1 DesktopUser DesktopUser   26054 2011-01-15 13:15 42AB1ED9d01
-rw------- 1 DesktopUser DesktopUser   20774 2011-01-15 13:25 42D69CB1d01
-rw------- 1 DesktopUser DesktopUser   58691 2011-01-15 09:40 42EDEE51d01
-rw------- 1 DesktopUser DesktopUser  148011 2011-01-15 09:26 431B4BEAd01
-rw------- 1 DesktopUser DesktopUser   57098 2011-01-15 13:17 43E06119d01
-rw------- 1 DesktopUser DesktopUser   22231 2011-01-15 13:25 450959A7d01
-rw------- 1 DesktopUser DesktopUser   18506 2011-01-15 13:19 474DB75Fd01
-rw------- 1 DesktopUser DesktopUser   59077 2011-01-15 13:18 474FC0ADd01
-rw------- 1 DesktopUser DesktopUser   22200 2011-01-15 13:19 4A7FBAD9d01
-rw------- 1 DesktopUser DesktopUser   42160 2011-01-15 13:19 4A90759Cd01
-rw------- 1 DesktopUser DesktopUser   19842 2011-01-15 13:25 4B4D2748d01
-rw------- 1 DesktopUser DesktopUser   20574 2011-01-15 13:19 4DCF92BDd01
-rw------- 1 DesktopUser DesktopUser   26811 2011-01-15 13:19 4DEF9A6Cd01
-rw------- 1 DesktopUser DesktopUser   17690 2011-01-15 13:17 504043A6d01
-rw------- 1 DesktopUser DesktopUser   80447 2011-01-15 09:40 50955769d01
-rw------- 1 DesktopUser DesktopUser   19297 2011-01-15 13:17 53CF15D5d01
-rw------- 1 DesktopUser DesktopUser   23980 2011-01-15 13:25 53DCF93Ad01
-rw------- 1 DesktopUser DesktopUser   25326 2011-01-15 13:17 55F24B6Bd01
-rw------- 1 DesktopUser DesktopUser   20483 2011-01-15 13:24 56346737d01
-rw------- 1 DesktopUser DesktopUser   19913 2011-01-15 13:25 574089D4d01
-rw------- 1 DesktopUser DesktopUser   21686 2011-01-15 13:25 5832500Ed01
-rw------- 1 DesktopUser DesktopUser   19703 2011-01-15 13:17 583369DEd01
-rw------- 1 DesktopUser DesktopUser   38688 2011-01-15 13:20 5898C908d01
-rw------- 1 DesktopUser DesktopUser   30395 2011-01-15 09:26 58A65A13d01
-rw------- 1 DesktopUser DesktopUser   22210 2011-01-15 13:17 59E958F2d01
-rw------- 1 DesktopUser DesktopUser   23530 2011-01-15 13:25 5A80F9B5d01
-rw------- 1 DesktopUser DesktopUser   23042 2011-01-15 13:25 5AA74CBEd01
-rw------- 1 DesktopUser DesktopUser   18490 2011-01-15 13:25 5AEB624Cd01
-rw------- 1 DesktopUser DesktopUser   21350 2011-01-15 13:25 5AED1EB0d01
-rw------- 1 DesktopUser DesktopUser   59309 2011-01-15 13:25 5B891AA2d01
-rw------- 1 DesktopUser DesktopUser   22161 2011-01-15 13:25 5BDEF791d01
-rw------- 1 DesktopUser DesktopUser   35387 2011-01-15 08:38 5BFCA42Ad01
-rw------- 1 DesktopUser DesktopUser   16926 2011-01-15 13:19 5C00A335d01
-rw------- 1 DesktopUser DesktopUser   79547 2011-01-15 13:19 5C641A3Ed01
-rw------- 1 DesktopUser DesktopUser   17499 2011-01-15 13:15 5CC22546d01
-rw------- 1 DesktopUser DesktopUser   29018 2011-01-15 08:49 5D372ACCd01
-rw------- 1 DesktopUser DesktopUser   27372 2011-01-15 13:19 5DB93208d01
-rw------- 1 DesktopUser DesktopUser   57133 2011-01-15 13:25 5EE671C9d01
-rw------- 1 DesktopUser DesktopUser   52988 2011-01-15 13:25 5F052DFEd01
-rw------- 1 DesktopUser DesktopUser   20849 2011-01-15 13:24 5FB00806d01
-rw------- 1 DesktopUser DesktopUser   22346 2011-01-15 13:25 5FD0FC1Bd01
-rw------- 1 DesktopUser DesktopUser   22031 2011-01-15 13:25 5FEC1CDFd01
-rw------- 1 DesktopUser DesktopUser   22192 2011-01-15 13:25 60E23D3Ed01
-rw------- 1 DesktopUser DesktopUser   22074 2011-01-15 13:25 614A6372d01
-rw------- 1 DesktopUser DesktopUser   29571 2011-01-15 13:09 61E2478Fd01
-rw------- 1 DesktopUser DesktopUser   54347 2011-01-15 13:19 63487055d01
-rw------- 1 DesktopUser DesktopUser   33663 2011-01-15 13:20 645FFF1Ed01
-rw------- 1 DesktopUser DesktopUser   21264 2011-01-15 13:25 65DF887Dd01
-rw------- 1 DesktopUser DesktopUser   29837 2011-01-15 13:15 66024AE6d01
-rw------- 1 DesktopUser DesktopUser   48622 2011-01-15 09:26 6682E6D9d01
-rw------- 1 DesktopUser DesktopUser   22239 2011-01-15 13:24 67971834d01
-rw------- 1 DesktopUser DesktopUser   80360 2011-01-15 13:36 67E111DBd01
-rw------- 1 DesktopUser DesktopUser   18717 2011-01-15 13:28 6A8D1B67d01
-rw------- 1 DesktopUser DesktopUser   51181 2011-01-15 13:25 6A9830B6d01
-rw------- 1 DesktopUser DesktopUser   21720 2011-01-15 13:24 6B02B6DEd01
-rw------- 1 DesktopUser DesktopUser   34062 2011-01-15 09:19 6B06B8DFd01
-rw------- 1 DesktopUser DesktopUser   22387 2011-01-15 13:20 6B5780E8d01
-rw------- 1 DesktopUser DesktopUser   18905 2011-01-15 13:17 6BBA59DCd01
-rw------- 1 DesktopUser DesktopUser   28061 2011-01-15 09:04 6BCB3B8Bd01
-rw------- 1 DesktopUser DesktopUser   29619 2011-01-15 13:20 6BF8EEF3d01
-rw------- 1 DesktopUser DesktopUser   19850 2011-01-15 13:25 6C1860C6d01
-rw------- 1 DesktopUser DesktopUser   67011 2011-01-15 13:25 6CB5B602d01
-rw------- 1 DesktopUser DesktopUser   25366 2011-01-15 13:09 6CCD58DCd01
-rw------- 1 DesktopUser DesktopUser   26866 2011-01-15 13:09 6CE38658d01
-rw------- 1 DesktopUser DesktopUser   18884 2011-01-15 13:25 6FF87D4Dd01
-rw------- 1 DesktopUser DesktopUser  113063 2011-01-15 13:36 703416E7d01
-rw------- 1 DesktopUser DesktopUser   28749 2011-01-15 09:04 7062567Dd01
-rw------- 1 DesktopUser DesktopUser   18012 2011-01-15 13:17 710DE005d01
-rw------- 1 DesktopUser DesktopUser   86392 2011-01-15 13:30 73A25555d01
-rw------- 1 DesktopUser DesktopUser   22709 2011-01-15 13:24 73AEDBFBd01
-rw------- 1 DesktopUser DesktopUser   74840 2011-01-15 08:49 741C093Cd01
-rw------- 1 DesktopUser DesktopUser   21327 2011-01-15 13:25 74F5876Fd01
-rw------- 1 DesktopUser DesktopUser   21781 2011-01-15 13:24 75CF3F89d01
-rw------- 1 DesktopUser DesktopUser   40795 2011-01-15 13:20 76354385d01
-rw------- 1 DesktopUser DesktopUser   22386 2011-01-15 13:24 7684B957d01
-rw------- 1 DesktopUser DesktopUser   22255 2011-01-15 13:24 770B371Cd01
-rw------- 1 DesktopUser DesktopUser   16545 2011-01-15 13:25 784B079Ed01
-rw------- 1 DesktopUser DesktopUser   21519 2011-01-15 13:25 789030E4d01
-rw------- 1 DesktopUser DesktopUser   37263 2011-01-15 09:26 789634D3d01
-rw------- 1 DesktopUser DesktopUser   25523 2011-01-15 13:25 78CB12C3d01
-rw------- 1 DesktopUser DesktopUser   22634 2011-01-15 13:25 7AA48EBBd01
-rw------- 1 DesktopUser DesktopUser   20414 2011-01-15 13:25 7ABC1C8Dd01
-rw------- 1 DesktopUser DesktopUser   18143 2011-01-15 09:27 7ACBB7C3d01
-rw------- 1 DesktopUser DesktopUser   17502 2011-01-15 13:25 7D246C2Bd01
-rw------- 1 DesktopUser DesktopUser   19371 2011-01-15 13:25 7D8B88F9d01
-rw------- 1 DesktopUser DesktopUser   21337 2011-01-15 13:17 7DBCDF3Cd01
-rw------- 1 DesktopUser DesktopUser   26563 2011-01-15 13:19 7E04B1D9d01
-rw------- 1 DesktopUser DesktopUser   18646 2011-01-15 13:28 7E268F2Bd01
-rw------- 1 DesktopUser DesktopUser   19656 2011-01-15 13:28 7EF08CADd01
-rw------- 1 DesktopUser DesktopUser   61073 2011-01-15 13:16 7F6311E2d01
-rw------- 1 DesktopUser DesktopUser   21005 2011-01-15 13:25 7F837442d01
-rw------- 1 DesktopUser DesktopUser   20606 2011-01-15 13:25 7FC05675d01
-rw------- 1 DesktopUser DesktopUser   23040 2011-01-15 13:25 809D590Cd01
-rw------- 1 DesktopUser DesktopUser   55805 2011-01-15 09:27 80DA202Fd01
-rw------- 1 DesktopUser DesktopUser   16713 2011-01-15 13:17 81EEDE1Ed01
-rw------- 1 DesktopUser DesktopUser  147848 2011-01-15 13:36 822562EFd01
-rw------- 1 DesktopUser DesktopUser   61309 2011-01-15 13:16 83917506d01
-rw------- 1 DesktopUser DesktopUser   17215 2011-01-15 13:15 83C704CCd01
-rw------- 1 DesktopUser DesktopUser   19488 2011-01-15 13:17 84CD7111d01
-rw------- 1 DesktopUser DesktopUser   22239 2011-01-15 13:25 853218B3d01
-rw------- 1 DesktopUser DesktopUser   20646 2011-01-15 13:25 866C0CA2d01
-rw------- 1 DesktopUser DesktopUser   41058 2011-01-15 13:25 86CF6720d01
-rw------- 1 DesktopUser DesktopUser   71525 2011-01-15 13:18 882B7074d01
-rw------- 1 DesktopUser DesktopUser  101412 2011-01-15 09:41 88D80EB1d01
-rw------- 1 DesktopUser DesktopUser   23004 2011-01-15 09:27 88E6D21Ed01
-rw------- 1 DesktopUser DesktopUser   24819 2011-01-15 13:19 89165237d01
-rw------- 1 DesktopUser DesktopUser   16902 2011-01-15 09:40 893A5247d01
-rw------- 1 DesktopUser DesktopUser   21448 2011-01-15 13:24 8A0491FCd01
-rw------- 1 DesktopUser DesktopUser   24789 2011-01-15 09:27 8A74792Cd01
-rw------- 1 DesktopUser DesktopUser   21058 2011-01-15 13:24 8AF2B365d01
-rw------- 1 DesktopUser DesktopUser   24304 2011-01-15 13:19 8F1FF9ABd01
-rw------- 1 DesktopUser DesktopUser   18540 2011-01-15 13:25 8F33619Fd01
-rw------- 1 DesktopUser DesktopUser   20203 2011-01-15 13:25 8F3AE542d01
-rw------- 1 DesktopUser DesktopUser   19753 2011-01-15 13:24 8F665ACEd01
-rw------- 1 DesktopUser DesktopUser   45936 2011-01-15 13:24 8F9F4A8Bd01
-rw------- 1 DesktopUser DesktopUser   64640 2011-01-15 13:16 8FB4F392d01
-rw------- 1 DesktopUser DesktopUser   47873 2011-01-15 13:25 907F11A1d01
-rw------- 1 DesktopUser DesktopUser   17786 2011-01-15 08:38 91081CBFd01
-rw------- 1 DesktopUser DesktopUser   35517 2011-01-15 13:25 911D3FF0d01
-rw------- 1 DesktopUser DesktopUser   50039 2011-01-15 13:20 9254CA56d01
-rw------- 1 DesktopUser DesktopUser   22046 2011-01-15 13:15 9257CB8Fd01
-rw------- 1 DesktopUser DesktopUser   20891 2011-01-15 13:36 92CD5C8Dd01
-rw------- 1 DesktopUser DesktopUser   28700 2011-01-15 08:49 945703FDd01
-rw------- 1 DesktopUser DesktopUser   68281 2011-01-15 13:17 94B26850d01
-rw------- 1 DesktopUser DesktopUser   17136 2011-01-15 13:25 94CB6466d01
-rw------- 1 DesktopUser DesktopUser  112257 2011-01-15 13:34 94D8D34Bd01
-rw------- 1 DesktopUser DesktopUser   60599 2011-01-15 13:18 950456C7d01
-rw------- 1 DesktopUser DesktopUser   22269 2011-01-15 13:25 9609B458d01
-rw------- 1 DesktopUser DesktopUser   63656 2011-01-15 13:20 96C2E66Cd01
-rw------- 1 DesktopUser DesktopUser   23885 2011-01-15 08:49 978BDDA9d01
-rw------- 1 DesktopUser DesktopUser   44058 2011-01-15 13:20 97E55E17d01
-rw------- 1 DesktopUser DesktopUser   21068 2011-01-15 13:25 98213757d01
-rw------- 1 DesktopUser DesktopUser  113528 2011-01-15 13:29 99A394A8d01
-rw------- 1 DesktopUser DesktopUser   17350 2011-01-15 13:17 9A3C8781d01
-rw------- 1 DesktopUser DesktopUser   47473 2011-01-15 09:27 9B4A2DF5d01
-rw------- 1 DesktopUser DesktopUser   20002 2011-01-15 13:28 9BE84708d01
-rw------- 1 DesktopUser DesktopUser   21166 2011-01-15 09:25 9C5B265Ed01
-rw------- 1 DesktopUser DesktopUser   37390 2011-01-15 08:38 9D80B995d01
-rw------- 1 DesktopUser DesktopUser   58347 2011-01-15 13:25 9E4FA58Ed01
-rw------- 1 DesktopUser DesktopUser   26331 2011-01-15 13:25 A02A333Ed01
-rw------- 1 DesktopUser DesktopUser   19215 2011-01-15 13:19 A0A063F4d01
-rw------- 1 DesktopUser DesktopUser   24124 2011-01-15 13:24 A128942Ed01
-rw------- 1 DesktopUser DesktopUser   20890 2011-01-15 13:24 A182298Bd01
-rw------- 1 DesktopUser DesktopUser   64161 2011-01-15 13:24 A1DACE8Ad01
-rw------- 1 DesktopUser DesktopUser   24193 2011-01-15 13:25 A2313C33d01
-rw------- 1 DesktopUser DesktopUser   16397 2011-01-15 13:15 A3B265B0d01
-rw------- 1 DesktopUser DesktopUser   22707 2011-01-15 13:17 A42F018Ed01
-rw------- 1 DesktopUser DesktopUser   68524 2011-01-15 13:18 A495C8D2d01
-rw------- 1 DesktopUser DesktopUser   28736 2011-01-15 13:24 A535FCD0d01
-rw------- 1 DesktopUser DesktopUser   18450 2011-01-15 13:17 A55D17AFd01
-rw------- 1 DesktopUser DesktopUser   18457 2011-01-15 13:19 A5BB2EDBd01
-rw------- 1 DesktopUser DesktopUser   31049 2011-01-15 09:26 A68FCB6Ad01
-rw------- 1 DesktopUser DesktopUser   20143 2011-01-15 13:10 A73D018Fd01
-rw------- 1 DesktopUser DesktopUser   27540 2011-01-15 13:09 A7531EE3d01
-rw------- 1 DesktopUser DesktopUser   27550 2011-01-15 13:25 A765EDE4d01
-rw------- 1 DesktopUser DesktopUser   22719 2011-01-15 13:24 A7A23293d01
-rw------- 1 DesktopUser DesktopUser   20163 2011-01-15 13:25 A87E56C7d01
-rw------- 1 DesktopUser DesktopUser   17740 2011-01-15 13:17 A9752B66d01
-rw------- 1 DesktopUser DesktopUser   21174 2011-01-15 13:17 AB69473Dd01
-rw------- 1 DesktopUser DesktopUser   22740 2011-01-15 13:25 AC0C1A07d01
-rw------- 1 DesktopUser DesktopUser   16681 2011-01-15 13:24 ADB082CCd01
-rw------- 1 DesktopUser DesktopUser   64810 2011-01-15 13:16 ADCCF16Cd01
-rw------- 1 DesktopUser DesktopUser   22707 2011-01-15 09:26 AE8E9721d01
-rw------- 1 DesktopUser DesktopUser   22007 2011-01-15 13:25 AF10D35Ed01
-rw------- 1 DesktopUser DesktopUser   21915 2011-01-15 13:19 AF1EDDBFd01
-rw------- 1 DesktopUser DesktopUser   21178 2011-01-15 13:25 B31F7852d01
-rw------- 1 DesktopUser DesktopUser   17048 2011-01-15 13:19 B33D0B00d01
-rw------- 1 DesktopUser DesktopUser   26429 2011-01-15 13:09 B42A31B7d01
-rw------- 1 DesktopUser DesktopUser   20065 2011-01-15 13:25 B54ACA4Cd01
-rw------- 1 DesktopUser DesktopUser   33810 2011-01-15 13:24 B6C7869Bd01
-rw------- 1 DesktopUser DesktopUser   22098 2011-01-15 13:25 B74CDC2Dd01
-rw------- 1 DesktopUser DesktopUser   16704 2011-01-15 13:26 B88C0E3Ed01
-rw------- 1 DesktopUser DesktopUser   19638 2011-01-15 13:25 B8A56F29d01
-rw------- 1 DesktopUser DesktopUser   31656 2011-01-15 09:26 B910713Ad01
-rw------- 1 DesktopUser DesktopUser   69354 2011-01-15 13:17 B992103Fd01
-rw------- 1 DesktopUser DesktopUser   21031 2011-01-15 13:24 B9EB05D2d01
-rw------- 1 DesktopUser DesktopUser   71396 2011-01-15 13:19 BA55BFE2d01
-rw------- 1 DesktopUser DesktopUser   57459 2011-01-15 13:19 BA6432C8d01
-rw------- 1 DesktopUser DesktopUser   22314 2011-01-15 13:25 BBA07C6Dd01
-rw------- 1 DesktopUser DesktopUser  105046 2011-01-15 13:19 BBC530C3d01
-rw------- 1 DesktopUser DesktopUser   22378 2011-01-15 13:24 BC2F77FCd01
-rw------- 1 DesktopUser DesktopUser   20271 2011-01-15 13:25 BCBDDCB4d01
-rw------- 1 DesktopUser DesktopUser   84178 2011-01-15 13:16 BCFF4E05d01
-rw------- 1 DesktopUser DesktopUser   17164 2011-01-15 13:17 BE06BD8Ad01
-rw------- 1 DesktopUser DesktopUser   22201 2011-01-15 13:24 BE3BEFE9d01
-rw------- 1 DesktopUser DesktopUser   30641 2011-01-15 13:19 BE7611F6d01
-rw------- 1 DesktopUser DesktopUser   33222 2011-01-15 13:20 BF4A33BAd01
-rw------- 1 DesktopUser DesktopUser   63681 2011-01-15 13:16 C037497Dd01
-rw------- 1 DesktopUser DesktopUser  102744 2011-01-15 13:19 C103E737d01
-rw------- 1 DesktopUser DesktopUser  105044 2011-01-15 13:24 C1997A72d01
-rw------- 1 DesktopUser DesktopUser   21804 2011-01-15 13:25 C1A4769Ed01
-rw------- 1 DesktopUser DesktopUser   18509 2011-01-15 13:19 C221ACCFd01
-rw------- 1 DesktopUser DesktopUser   37015 2011-01-15 08:49 C3C03BEFd01
-rw------- 1 DesktopUser DesktopUser   17317 2011-01-15 13:28 C4B50F5Fd01
-rw------- 1 DesktopUser DesktopUser   51596 2011-01-15 13:25 C4FEFDEAd01
-rw------- 1 DesktopUser DesktopUser   20954 2011-01-15 13:24 C5DE39F5d01
-rw------- 1 DesktopUser DesktopUser   22323 2011-01-15 13:25 C7B893D5d01
-rw------- 1 DesktopUser DesktopUser   20248 2011-01-15 13:25 C9BF388Cd01
-rw------- 1 DesktopUser DesktopUser  112808 2011-01-15 13:16 C9C536D9d01
-rw------- 1 DesktopUser DesktopUser   41364 2011-01-15 13:24 C9F0CAEBd01
-rw------- 1 DesktopUser DesktopUser   18743 2011-01-15 13:24 CA1086B2d01
-rw------- 1 DesktopUser DesktopUser   22821 2011-01-15 13:25 CA26C27Ad01
-rw------- 1 DesktopUser DesktopUser  176871 2011-01-15 13:37 CA2D3EE0d01
-rw------- 1 DesktopUser DesktopUser   17958 2011-01-15 13:17 CA763CF4d01
-rw------- 1 DesktopUser DesktopUser   18639 2011-01-15 13:25 CAC700B4d01
-rw------- 1 DesktopUser DesktopUser 1525756 2011-01-15 13:38 _CACHE_001_
-rw------- 1 DesktopUser DesktopUser 1898664 2011-01-15 13:37 _CACHE_002_
-rw------- 1 DesktopUser DesktopUser 8162077 2011-01-15 13:37 _CACHE_003_
-rw------- 1 DesktopUser DesktopUser     276 2011-01-15 08:38 _CACHE_MAP_
-rw------- 1 DesktopUser DesktopUser   21593 2011-01-15 13:24 CDFC59C0d01
-rw------- 1 DesktopUser DesktopUser   21788 2011-01-15 13:25 CF84C499d01
-rw------- 1 DesktopUser DesktopUser   22715 2011-01-15 13:24 D13A8C8Dd01
-rw------- 1 DesktopUser DesktopUser   20976 2011-01-15 13:24 D228DC70d01
-rw------- 1 DesktopUser DesktopUser   19297 2011-01-15 13:19 D2623BC7d01
-rw------- 1 DesktopUser DesktopUser   50754 2011-01-15 13:25 D5C83506d01
-rw------- 1 DesktopUser DesktopUser   19186 2011-01-15 13:25 D69E2238d01
-rw------- 1 DesktopUser DesktopUser   39530 2011-01-15 13:24 D6E396C9d01
-rw------- 1 DesktopUser DesktopUser   16860 2011-01-15 13:25 D723B672d01
-rw------- 1 DesktopUser DesktopUser   21170 2011-01-15 13:25 D7EB6697d01
-rw------- 1 DesktopUser DesktopUser   21066 2011-01-15 08:49 D7FF2707d01
-rw------- 1 DesktopUser DesktopUser   20937 2011-01-15 13:25 D876291Ed01
-rw------- 1 DesktopUser DesktopUser   20721 2011-01-15 13:24 D93F21F0d01
-rw------- 1 DesktopUser DesktopUser   35345 2011-01-15 13:19 D9E0DA55d01
-rw------- 1 DesktopUser DesktopUser   35588 2011-01-15 13:19 DA3A4837d01
-rw------- 1 DesktopUser DesktopUser   23568 2011-01-15 13:25 DAD88D3Cd01
-rw------- 1 DesktopUser DesktopUser   18312 2011-01-15 13:17 DAD91A90d01
-rw------- 1 DesktopUser DesktopUser   29541 2011-01-15 09:26 DB5E1227d01
-rw------- 1 DesktopUser DesktopUser   70838 2011-01-15 13:16 DB93AC94d01
-rw------- 1 DesktopUser DesktopUser   27057 2011-01-15 13:25 DBBAE540d01
-rw------- 1 DesktopUser DesktopUser   22787 2011-01-15 13:19 DC847ECAd01
-rw------- 1 DesktopUser DesktopUser   73669 2011-01-15 13:27 DD03FBF8d01
-rw------- 1 DesktopUser DesktopUser   16900 2011-01-15 08:38 DD94E7F2d01
-rw------- 1 DesktopUser DesktopUser   21433 2011-01-15 13:17 DDB1026Dd01
-rw------- 1 DesktopUser DesktopUser   19133 2011-01-15 13:19 DF2B92F1d01
-rw------- 1 DesktopUser DesktopUser   24223 2011-01-15 13:25 DF7CAB2Ad01
-rw------- 1 DesktopUser DesktopUser  170106 2011-01-15 13:31 E03C70DBd01
-rw------- 1 DesktopUser DesktopUser   16525 2011-01-15 13:28 E55C4C79d01
-rw------- 1 DesktopUser DesktopUser   56575 2011-01-15 13:16 E7F64A3Bd01
-rw------- 1 DesktopUser DesktopUser   23257 2011-01-15 13:19 E89285DBd01
-rw------- 1 DesktopUser DesktopUser   55014 2011-01-15 13:19 E9A0F713d01
-rw------- 1 DesktopUser DesktopUser   19575 2011-01-15 13:19 EAD25134d01
-rw------- 1 DesktopUser DesktopUser   18367 2011-01-15 13:19 EB47D838d01
-rw------- 1 DesktopUser DesktopUser   20905 2011-01-15 13:25 EC3ED120d01
-rw------- 1 DesktopUser DesktopUser   93055 2011-01-15 09:26 EC651522d01
-rw------- 1 DesktopUser DesktopUser   19556 2011-01-15 13:25 ED425CDAd01
-rw------- 1 DesktopUser DesktopUser   20347 2011-01-15 13:15 EE572D64d01
-rw------- 1 DesktopUser DesktopUser   19029 2011-01-15 13:25 EE728EDBd01
-rw------- 1 DesktopUser DesktopUser   99634 2011-01-15 13:25 EFBD94A9d01
-rw------- 1 DesktopUser DesktopUser   40418 2011-01-15 09:41 F076940Ed01
-rw------- 1 DesktopUser DesktopUser   17459 2011-01-15 13:09 F1109B7Bd01
-rw------- 1 DesktopUser DesktopUser   16710 2011-01-15 08:38 F17BC44Dd01
-rw------- 1 DesktopUser DesktopUser   21171 2011-01-15 13:25 F20CC592d01
-rw------- 1 DesktopUser DesktopUser   21737 2011-01-15 13:25 F35E9E70d01
-rw------- 1 DesktopUser DesktopUser   22133 2011-01-15 13:25 F48A719Fd01
-rw------- 1 DesktopUser DesktopUser   16777 2011-01-15 13:25 F52C64D0d01
-rw------- 1 DesktopUser DesktopUser   39880 2011-01-15 13:27 F55CDEECd01
-rw------- 1 DesktopUser DesktopUser   19550 2011-01-15 13:20 F77735E6d01
-rw------- 1 DesktopUser DesktopUser   22504 2011-01-15 13:19 FA71A827d01
-rw------- 1 DesktopUser DesktopUser  105539 2011-01-15 09:19 FADCC682d01
-rw------- 1 DesktopUser DesktopUser   61621 2011-01-15 13:25 FB0A0B7Fd01
-rw------- 1 DesktopUser DesktopUser   37013 2011-01-15 13:18 FB772DB3d01
-rw------- 1 DesktopUser DesktopUser  112302 2011-01-15 13:16 FD48F654d01
-rw------- 1 DesktopUser DesktopUser   21780 2011-01-15 13:24 FE3ABA67d01
-rw------- 1 DesktopUser DesktopUser   55087 2011-01-15 13:30 FE481DACd01
-rw------- 1 DesktopUser DesktopUser   21438 2011-01-15 13:25 FE597FE6d01
-rw------- 1 DesktopUser DesktopUser  113746 2011-01-15 13:31 FEBCB7EBd01
-rw------- 1 DesktopUser DesktopUser   16826 2011-01-15 13:17 FF8FFEDCd01

./firefox/bc3huk63.default/chrome:
total 8
-rw-r--r-- 1 DesktopUser DesktopUser 959 2010-08-11 21:11 userChrome-example.css
-rw-r--r-- 1 DesktopUser DesktopUser 663 2010-08-11 21:11 userContent-example.css

./firefox/bc3huk63.default/extensions:
total 8
drwxr-xr-x 6 DesktopUser DesktopUser 4096 2010-12-12 09:16 {c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}
drwxr-xr-x 7 DesktopUser DesktopUser 4096 2010-12-30 10:54 {d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}

./firefox/bc3huk63.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}:
total 24
drwxr-xr-x 2 DesktopUser DesktopUser 4096 2010-12-12 09:16 chrome
-rw-r--r-- 1 DesktopUser DesktopUser  230 2009-03-31 14:43 chrome.manifest
drwxr-xr-x 2 DesktopUser DesktopUser 4096 2010-12-12 09:16 content
drwxr-xr-x 3 DesktopUser DesktopUser 4096 2010-12-12 09:16 defaults
-rw-r--r-- 1 DesktopUser DesktopUser 1115 2010-12-10 20:11 install.rdf
drwxr-xr-x 2 DesktopUser DesktopUser 4096 2010-12-12 09:16 skin

./firefox/bc3huk63.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}/chrome:
total 0

./firefox/bc3huk63.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}/content:
total 44
-rw-r--r-- 1 DesktopUser DesktopUser 11371 2010-12-10 20:08 downloadyoutubevideosasmp.js
-rw-r--r-- 1 DesktopUser DesktopUser  1386 2009-06-14 09:55 options.xul
-rw-r--r-- 1 DesktopUser DesktopUser  2691 2019-09-25 22:40 prefman.js
-rw-r--r-- 1 DesktopUser DesktopUser 15161 2010-11-22 14:46 script-compiler.js
-rw-r--r-- 1 DesktopUser DesktopUser   454 2019-09-25 22:40 script-compiler-overlay.xul
-rw-r--r-- 1 DesktopUser DesktopUser  3454 2019-09-25 22:40 xmlhttprequester.js

./firefox/bc3huk63.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}/defaults:
total 4
drwxr-xr-x 2 DesktopUser DesktopUser 4096 2010-12-12 09:16 preferences

./firefox/bc3huk63.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}/defaults/preferences:
total 4
-rw-r--r-- 1 DesktopUser DesktopUser 63 2009-06-13 10:49 defaults.js

./firefox/bc3huk63.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}/skin:
total 4
-rw-r--r-- 1 DesktopUser DesktopUser 2826 2009-04-22 12:01 youtube.png

./firefox/bc3huk63.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}:
total 52
drwxr-xr-x 2 DesktopUser DesktopUser  4096 2010-12-30 10:54 chrome
-rw-r--r-- 1 DesktopUser DesktopUser  5090 2010-12-23 16:06 chrome.manifest
drwxr-xr-x 2 DesktopUser DesktopUser  4096 2010-12-30 10:54 components
drwxr-xr-x 3 DesktopUser DesktopUser  4096 2010-12-30 10:54 defaults
-rw-r--r-- 1 DesktopUser DesktopUser   708 2010-12-23 16:06 icon.png
-rw-r--r-- 1 DesktopUser DesktopUser 18200 2010-12-23 16:06 install.rdf
drwxr-xr-x 2 DesktopUser DesktopUser  4096 2010-12-30 10:54 META-INF
drwxr-xr-x 2 DesktopUser DesktopUser  4096 2010-12-30 10:54 modules

./firefox/bc3huk63.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/chrome:
total 1456
-rw-r--r-- 1 DesktopUser DesktopUser 1489925 2010-12-23 16:06 adblockplus.jar

./firefox/bc3huk63.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/components:
total 4
-rw-r--r-- 1 DesktopUser DesktopUser 3841 2010-12-23 16:06 Initializer.js

./firefox/bc3huk63.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/defaults:
total 8
-rw-r--r-- 1 DesktopUser DesktopUser  137 2010-12-23 16:06 patterns.ini
drwxr-xr-x 2 DesktopUser DesktopUser 4096 2010-12-30 10:54 preferences

./firefox/bc3huk63.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/defaults/preferences:
total 4
-rw-r--r-- 1 DesktopUser DesktopUser 2209 2010-12-23 16:06 adblockplus.js

./firefox/bc3huk63.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/META-INF:
total 16
-rw-r--r-- 1 DesktopUser DesktopUser 3287 2010-12-23 16:06 manifest.mf
-rw-r--r-- 1 DesktopUser DesktopUser 4507 2010-12-23 16:06 zigbert.rsa
-rw-r--r-- 1 DesktopUser DesktopUser 3395 2010-12-23 16:06 zigbert.sf

./firefox/bc3huk63.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/modules:
total 240
-rw-r--r-- 1 DesktopUser DesktopUser  8080 2010-12-23 16:06 AppIntegrationFennec.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 37875 2010-12-23 16:06 AppIntegration.jsm
-rw-r--r-- 1 DesktopUser DesktopUser  6083 2010-12-23 16:06 Bootstrap.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 17897 2010-12-23 16:06 ContentPolicy.jsm
-rw-r--r-- 1 DesktopUser DesktopUser  7756 2010-12-23 16:06 ElemHide.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 20916 2010-12-23 16:06 FilterClasses.jsm
-rw-r--r-- 1 DesktopUser DesktopUser  5535 2010-12-23 16:06 FilterListener.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 19984 2010-12-23 16:06 FilterStorage.jsm
-rw-r--r-- 1 DesktopUser DesktopUser  9000 2010-12-23 16:06 Matcher.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 14882 2010-12-23 16:06 ObjectTabs.jsm
-rw-r--r-- 1 DesktopUser DesktopUser  7328 2010-12-23 16:06 Prefs.jsm
-rw-r--r-- 1 DesktopUser DesktopUser  5562 2010-12-23 16:06 Public.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 10647 2010-12-23 16:06 RequestNotifier.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 11571 2010-12-23 16:06 SubscriptionClasses.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 17633 2010-12-23 16:06 Synchronizer.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 13915 2010-12-23 16:06 Utils.jsm

./firefox/bc3huk63.default/minidumps:
total 0

./firefox/bc3huk63.default/OfflineCache:
total 12
-rw-r--r-- 1 DesktopUser DesktopUser 10240 2010-12-17 00:07 index.sqlite

./firefox/Crash Reports:
total 36
-rw-r--r-- 1 DesktopUser DesktopUser   55 2010-09-26 21:41 crashreporter.ini
-rw------- 1 DesktopUser DesktopUser   10 2010-09-10 11:03 InstallTime20100825160138
-rw------- 1 DesktopUser DesktopUser   10 2010-09-18 15:23 InstallTime20100915180648
-rw------- 1 DesktopUser DesktopUser   10 2010-10-12 21:00 InstallTime20100922075949
-rw------- 1 DesktopUser DesktopUser   10 2010-10-21 11:13 InstallTime20101013125417
-rw------- 1 DesktopUser DesktopUser   10 2010-10-28 15:34 InstallTime20101027124735
-rw------- 1 DesktopUser DesktopUser   10 2010-12-09 20:42 InstallTime20101206121716
-rw------- 1 DesktopUser DesktopUser   10 2010-09-26 21:41 LastCrash
drwx------ 2 DesktopUser DesktopUser 4096 2010-09-26 21:41 pending
-rw-r--r-- 1 DesktopUser DesktopUser    0 2010-09-26 21:41 submit.log

./firefox/Crash Reports/pending:
total 0

```

---

### Post by WinstonChurchill on 2011-01-15
**EDIT: **Forgive the double-post... is it just me, or have the forums been pretty laggy lately?

---

### Post by bilkay on 2011-01-15
> **WinstonChurchill said:**
> Run firefox, and then post the output of the command: 'ps axu | grep firefox'

I get:
```

DesktopUser@DesktopBox:~$** ps axu | grep firefox**
DesktopUser  2433  0.0  0.0   4148   576 ?        S    08:36   0:00 /bin/sh /usr/lib/firefox-3.6.13/firefox
DesktopUser  2437  0.0  0.0   4148   576 ?        S    08:36   0:00 /bin/sh /usr/lib/firefox-3.6.13/run-mozilla.sh /usr/lib/firefox-3.6.13/firefox-bin
DesktopUser  2441  1.1  5.2 752124 213344 ?       Sl   08:36   3:30 /usr/lib/firefox-3.6.13/firefox-bin
DesktopUser  5153  0.0  0.0   8952   852 pts/3    S+   13:43   0:00 grep --color=auto firefox

```Also, I can confirm that Firefox should not be creating any files owned by root:
```

DesktopUser@DesktopBox:~/.mozilla$ ls -R -l
.:
total 8
drwx------ 3 DesktopUser DesktopUser 4096 2010-08-11 21:11 extensions
drwx------ 4 DesktopUser DesktopUser 4096 2010-09-10 11:03 firefox

./extensions:
total 4
drwxr-xr-x 2 DesktopUser DesktopUser 4096 2010-08-11 21:11 {ec8030f7-c20a-464f-9b0e-13a3a9e97384}

./extensions/{ec8030f7-c20a-464f-9b0e-13a3a9e97384}:
total 0

./firefox:
total 12
drwx------ 9 DesktopUser DesktopUser 4096 2011-01-15 13:38 bc3huk63.default
drwx------ 3 DesktopUser DesktopUser 4096 2010-12-09 20:42 Crash Reports
-rw-r--r-- 1 DesktopUser DesktopUser   94 2010-08-11 21:11 profiles.ini

./firefox/bc3huk63.default:
total 66452
drwxr-xr-x 2 DesktopUser DesktopUser     4096 2011-01-15 12:42 adblockplus
-rw-r--r-- 1 DesktopUser DesktopUser     4496 2011-01-14 20:47 blocklist.xml
drwx------ 2 DesktopUser DesktopUser     4096 2011-01-14 23:44 bookmarkbackups
-rw-r--r-- 1 DesktopUser DesktopUser    20162 2010-08-11 21:11 bookmarks.html
drwxr-xr-x 2 DesktopUser DesktopUser    12288 2011-01-15 13:37 Cache
-rw------- 1 DesktopUser DesktopUser   131072 2011-01-15 09:27 cert8.db
-rw------- 1 DesktopUser DesktopUser     1133 2011-01-04 00:09 cert_override.txt
drwxr-xr-x 2 DesktopUser DesktopUser     4096 2010-08-11 21:11 chrome
-rw------- 1 DesktopUser DesktopUser      168 2010-12-09 20:42 compatibility.ini
-rw-r--r-- 1 DesktopUser DesktopUser   150876 2010-12-30 10:54 compreg.dat
-rw-r--r-- 1 DesktopUser DesktopUser     7168 2011-01-15 08:38 content-prefs.sqlite
-rw-r--r-- 1 DesktopUser DesktopUser   207872 2011-01-15 13:38 cookies.sqlite
-rw-r--r-- 1 DesktopUser DesktopUser    84104 2011-01-15 13:38 cookies.sqlite-journal
-rw-r--r-- 1 DesktopUser DesktopUser    82944 2011-01-15 08:38 downloads.sqlite
drwxr-xr-x 4 DesktopUser DesktopUser     4096 2011-01-14 20:47 extensions
-rw-r--r-- 1 DesktopUser DesktopUser      800 2010-12-30 10:54 extensions.cache
-rw-r--r-- 1 DesktopUser DesktopUser      774 2010-12-30 10:54 extensions.ini
-rw-r--r-- 1 DesktopUser DesktopUser    26468 2011-01-09 00:18 extensions.rdf
-rw-r--r-- 1 DesktopUser DesktopUser    64512 2011-01-15 13:27 formhistory.sqlite
-rw------- 1 DesktopUser DesktopUser    16384 2011-01-14 23:44 key3.db
-rw-r--r-- 1 DesktopUser DesktopUser    13878 2011-01-15 08:38 localstore.rdf
lrwxrwxrwx 1 DesktopUser DesktopUser       15 2011-01-15 08:36 lock -> 127.0.1.1:+2441
-rw-r--r-- 1 DesktopUser DesktopUser    11956 2011-01-04 23:34 mimeTypes.rdf
drwx------ 2 DesktopUser DesktopUser     4096 2010-09-26 21:41 minidumps
drwx------ 2 DesktopUser DesktopUser     4096 2010-12-17 00:07 OfflineCache
-rw-r--r-- 1 DesktopUser DesktopUser     2048 2011-01-15 08:38 permissions.sqlite
-rw-r--r-- 1 DesktopUser DesktopUser        7 2010-11-09 01:29 persdict.dat
-rw-r--r-- 1 DesktopUser DesktopUser 10924032 2011-01-15 13:37 places.sqlite
-rw-r--r-- 1 DesktopUser DesktopUser        0 2011-01-15 13:37 places.sqlite-journal
-rw------- 1 DesktopUser DesktopUser     3179 2010-11-18 22:58 pluginreg.dat
-rw-r--r-- 1 DesktopUser DesktopUser    34959 2011-01-15 08:38 prefs.js
-rw-r--r-- 1 DesktopUser DesktopUser    14565 2011-01-15 08:36 search.json
-rw-r--r-- 1 DesktopUser DesktopUser     2048 2010-08-11 21:11 search.sqlite
-rw------- 1 DesktopUser DesktopUser    16384 2010-08-11 21:11 secmod.db
-rw------- 1 DesktopUser DesktopUser   216020 2010-08-31 16:42 sessionstore-1.js
-rw------- 1 DesktopUser DesktopUser    36615 2010-10-02 18:36 sessionstore-2.js
-rw------- 1 DesktopUser DesktopUser    69493 2010-12-16 20:48 sessionstore-3.js
-rw------- 1 DesktopUser DesktopUser   116033 2010-12-31 20:13 sessionstore-4.js
-rw------- 1 DesktopUser DesktopUser   106885 2011-01-15 13:38 sessionstore.js
-rw-r--r-- 1 DesktopUser DesktopUser    14336 2011-01-15 08:38 signons.sqlite
-rw-r--r-- 1 DesktopUser DesktopUser 51081216 2011-01-15 13:11 urlclassifier3.sqlite
-rw-r--r-- 1 DesktopUser DesktopUser      154 2011-01-15 08:40 urlclassifierkey3.txt
-rw-r--r-- 1 DesktopUser DesktopUser   292864 2011-01-15 08:38 webappsstore.sqlite
-rw-r--r-- 1 DesktopUser DesktopUser  2545663 2010-12-31 14:43 XPC.mfasl
-rw-r--r-- 1 DesktopUser DesktopUser   100823 2010-12-30 10:54 xpti.dat
-rw-r--r-- 1 DesktopUser DesktopUser  1517938 2011-01-15 08:38 XUL.mfasl

./firefox/bc3huk63.default/adblockplus:
total 1740
-rw-r--r-- 1 DesktopUser DesktopUser 298179 2011-01-14 20:43 patterns-backup1.ini
-rw-r--r-- 1 DesktopUser DesktopUser 298179 2011-01-13 16:07 patterns-backup2.ini
-rw-r--r-- 1 DesktopUser DesktopUser 298178 2011-01-12 22:52 patterns-backup3.ini
-rw-r--r-- 1 DesktopUser DesktopUser 298176 2011-01-11 22:55 patterns-backup4.ini
-rw-r--r-- 1 DesktopUser DesktopUser 297475 2011-01-10 23:30 patterns-backup5.ini
-rw-r--r-- 1 DesktopUser DesktopUser 285266 2011-01-15 12:42 patterns.ini

./firefox/bc3huk63.default/bookmarkbackups:
total 48
-rw------- 1 DesktopUser DesktopUser 5570 2011-01-05 14:24 bookmarks-2011-01-05.json
-rw------- 1 DesktopUser DesktopUser 5570 2011-01-09 00:55 bookmarks-2011-01-09.json
-rw------- 1 DesktopUser DesktopUser 5570 2011-01-11 00:16 bookmarks-2011-01-11.json
-rw------- 1 DesktopUser DesktopUser 5570 2011-01-12 02:18 bookmarks-2011-01-12.json
-rw------- 1 DesktopUser DesktopUser 5570 2011-01-13 15:42 bookmarks-2011-01-13.json
-rw------- 1 DesktopUser DesktopUser 5658 2011-01-14 23:44 bookmarks-2011-01-14.json

./firefox/bc3huk63.default/Cache:
total 24500
-rw------- 1 DesktopUser DesktopUser   20768 2011-01-15 13:25 003A2119d01
-rw------- 1 DesktopUser DesktopUser   21067 2011-01-15 13:25 0089868Bd01
-rw------- 1 DesktopUser DesktopUser   37708 2011-01-15 13:35 008C6605d01
-rw------- 1 DesktopUser DesktopUser   22589 2011-01-15 13:25 00D4A16Ad01
-rw------- 1 DesktopUser DesktopUser   67104 2011-01-15 13:18 0358E9E9d01
-rw------- 1 DesktopUser DesktopUser   22120 2011-01-15 13:25 036CD032d01
-rw------- 1 DesktopUser DesktopUser   27285 2011-01-15 13:25 044C52F6d01
-rw------- 1 DesktopUser DesktopUser   62545 2011-01-15 13:16 0636B572d01
-rw------- 1 DesktopUser DesktopUser   56826 2011-01-15 13:19 06CBDBAFd01
-rw------- 1 DesktopUser DesktopUser   22091 2011-01-15 13:25 06FA98BEd01
-rw------- 1 DesktopUser DesktopUser   16633 2011-01-15 13:17 079C1D5Ad01
-rw------- 1 DesktopUser DesktopUser   24707 2011-01-15 09:27 07B2C63Ed01
-rw------- 1 DesktopUser DesktopUser   22689 2011-01-15 08:49 0A138D66d01
-rw------- 1 DesktopUser DesktopUser   47112 2011-01-15 13:16 0AB09204d01
-rw------- 1 DesktopUser DesktopUser   23934 2011-01-15 13:25 0B294605d01
-rw------- 1 DesktopUser DesktopUser   25414 2011-01-15 09:27 0CC0A352d01
-rw------- 1 DesktopUser DesktopUser   21560 2011-01-15 13:24 0D860418d01
-rw------- 1 DesktopUser DesktopUser   42738 2011-01-15 13:25 0DBFA11Ed01
-rw------- 1 DesktopUser DesktopUser   16807 2011-01-15 13:15 0E84ACFBd01
-rw------- 1 DesktopUser DesktopUser   61450 2011-01-15 13:25 0FA6AB8Fd01
-rw------- 1 DesktopUser DesktopUser   22903 2011-01-15 13:17 1028BCC1d01
-rw------- 1 DesktopUser DesktopUser   18329 2011-01-15 13:19 11360347d01
-rw------- 1 DesktopUser DesktopUser   44324 2011-01-15 09:41 116972E3d01
-rw------- 1 DesktopUser DesktopUser   24354 2011-01-15 13:25 141E4789d01
-rw------- 1 DesktopUser DesktopUser   17745 2011-01-15 13:25 141F7BA9d01
-rw------- 1 DesktopUser DesktopUser   38291 2011-01-15 13:13 15507A27d01
-rw------- 1 DesktopUser DesktopUser   25942 2011-01-15 13:25 15E7E293d01
-rw------- 1 DesktopUser DesktopUser   16425 2011-01-15 13:28 176A8BE5d01
-rw------- 1 DesktopUser DesktopUser   22615 2011-01-15 13:25 182AABF7d01
-rw------- 1 DesktopUser DesktopUser   20128 2011-01-15 13:25 189ACC1Bd01
-rw------- 1 DesktopUser DesktopUser   99432 2011-01-15 13:16 18A6357Cd01
-rw------- 1 DesktopUser DesktopUser   47966 2011-01-15 13:20 18AB127Fd01
-rw------- 1 DesktopUser DesktopUser   21729 2011-01-15 13:25 191EF232d01
-rw------- 1 DesktopUser DesktopUser   78327 2011-01-15 13:18 1937894Cd01
-rw------- 1 DesktopUser DesktopUser   17924 2011-01-15 13:25 1ADC5365d01
-rw------- 1 DesktopUser DesktopUser   23841 2011-01-15 13:19 1BD3F9DBd01
-rw------- 1 DesktopUser DesktopUser   20367 2011-01-15 13:24 1BE1946Cd01
-rw------- 1 DesktopUser DesktopUser   18180 2011-01-15 13:17 1DCBE2E9d01
-rw------- 1 DesktopUser DesktopUser   18092 2011-01-15 13:25 1EEC6FB0d01
-rw------- 1 DesktopUser DesktopUser   21023 2011-01-15 13:24 1F1062B2d01
-rw------- 1 DesktopUser DesktopUser   22064 2011-01-15 13:24 20442686d01
-rw------- 1 DesktopUser DesktopUser   21441 2011-01-15 13:25 20F59014d01
-rw------- 1 DesktopUser DesktopUser   20714 2011-01-15 13:25 214E70BFd01
-rw------- 1 DesktopUser DesktopUser   19222 2011-01-15 13:25 21BECB8Ed01
-rw------- 1 DesktopUser DesktopUser   30500 2011-01-15 09:19 2227E43Ed01
-rw------- 1 DesktopUser DesktopUser   23178 2011-01-15 13:25 224F8890d01
-rw------- 1 DesktopUser DesktopUser   26525 2011-01-15 13:19 22606378d01
-rw------- 1 DesktopUser DesktopUser   52868 2011-01-15 13:25 226CDF57d01
-rw------- 1 DesktopUser DesktopUser   20621 2011-01-15 13:25 231806D3d01
-rw------- 1 DesktopUser DesktopUser   51105 2011-01-15 13:20 2339967Bd01
-rw------- 1 DesktopUser DesktopUser   49363 2011-01-15 13:25 23C55E64d01
-rw------- 1 DesktopUser DesktopUser   20748 2011-01-15 13:25 24050908d01
-rw------- 1 DesktopUser DesktopUser   67258 2011-01-15 13:19 24C4A355d01
-rw------- 1 DesktopUser DesktopUser   43722 2011-01-15 13:20 24FAA855d01
-rw------- 1 DesktopUser DesktopUser   73960 2011-01-15 13:18 25A9D175d01
-rw------- 1 DesktopUser DesktopUser   19558 2011-01-15 13:17 2619BC2Ed01
-rw------- 1 DesktopUser DesktopUser   23702 2011-01-15 13:17 2659BA05d01
-rw------- 1 DesktopUser DesktopUser   57839 2011-01-15 13:25 27B6D480d01
-rw------- 1 DesktopUser DesktopUser   22803 2011-01-15 13:25 27DE5BDCd01
-rw------- 1 DesktopUser DesktopUser   25504 2011-01-15 13:19 2A48E2F8d01
-rw------- 1 DesktopUser DesktopUser   23684 2011-01-15 09:27 2A661391d01
-rw------- 1 DesktopUser DesktopUser   22931 2011-01-15 13:17 2AC08176d01
-rw------- 1 DesktopUser DesktopUser  105708 2011-01-15 13:24 2BA162E8d01
-rw------- 1 DesktopUser DesktopUser   22605 2011-01-15 13:25 2CC1B7B4d01
-rw------- 1 DesktopUser DesktopUser   54145 2011-01-15 09:27 2CE0294Ad01
-rw------- 1 DesktopUser DesktopUser   19334 2011-01-15 09:39 2CE8D446d01
-rw------- 1 DesktopUser DesktopUser   23267 2011-01-15 13:25 2ED8856Ed01
-rw------- 1 DesktopUser DesktopUser   16456 2011-01-15 13:17 2F05B02Ad01
-rw------- 1 DesktopUser DesktopUser   22700 2011-01-15 13:25 2F9A59D6d01
-rw------- 1 DesktopUser DesktopUser   23548 2011-01-15 13:25 301F490Ed01
-rw------- 1 DesktopUser DesktopUser   22337 2011-01-15 13:25 3069340Cd01
-rw------- 1 DesktopUser DesktopUser   40083 2011-01-15 13:19 3083EF2Fd01
-rw------- 1 DesktopUser DesktopUser  107251 2011-01-15 13:09 3088B62Fd01
-rw------- 1 DesktopUser DesktopUser   46252 2011-01-15 13:25 32D59684d01
-rw------- 1 DesktopUser DesktopUser   52314 2011-01-15 13:20 34FED6BBd01
-rw------- 1 DesktopUser DesktopUser   26027 2011-01-15 13:37 354CCC4Cd01
-rw------- 1 DesktopUser DesktopUser  115117 2011-01-15 13:35 359AE592d01
-rw------- 1 DesktopUser DesktopUser   16921 2011-01-15 13:28 3735DF17d01
-rw------- 1 DesktopUser DesktopUser   22944 2011-01-15 13:25 37ED0BE0d01
-rw------- 1 DesktopUser DesktopUser   20136 2011-01-15 13:17 39427671d01
-rw------- 1 DesktopUser DesktopUser  103756 2011-01-15 09:04 3997108Ed01
-rw------- 1 DesktopUser DesktopUser   33619 2011-01-15 13:19 3C1A40C4d01
-rw------- 1 DesktopUser DesktopUser   23129 2011-01-15 13:25 3C4FB3F9d01
-rw------- 1 DesktopUser DesktopUser   20166 2011-01-15 13:25 3CB1513Bd01
-rw------- 1 DesktopUser DesktopUser   62544 2011-01-15 09:41 3D0D60C3d01
-rw------- 1 DesktopUser DesktopUser   17432 2011-01-15 13:15 3D9EF80Dd01
-rw------- 1 DesktopUser DesktopUser   17672 2011-01-15 13:25 3DCB3279d01
-rw------- 1 DesktopUser DesktopUser   21231 2011-01-15 13:24 3DF0D377d01
-rw------- 1 DesktopUser DesktopUser   35325 2011-01-15 13:19 3E0F69ABd01
-rw------- 1 DesktopUser DesktopUser   35206 2011-01-15 09:41 3EF5D178d01
-rw------- 1 DesktopUser DesktopUser   25482 2011-01-15 13:25 3F291EC1d01
-rw------- 1 DesktopUser DesktopUser   18314 2011-01-15 13:19 4010C90Ad01
-rw------- 1 DesktopUser DesktopUser   20442 2011-01-15 13:25 4044CA4Fd01
-rw------- 1 DesktopUser DesktopUser   21963 2011-01-15 13:24 41BAD6DAd01
-rw------- 1 DesktopUser DesktopUser   21648 2011-01-15 13:24 41F8F7C6d01
-rw------- 1 DesktopUser DesktopUser   21920 2011-01-15 13:24 420D0FA2d01
-rw------- 1 DesktopUser DesktopUser   26054 2011-01-15 13:15 42AB1ED9d01
-rw------- 1 DesktopUser DesktopUser   20774 2011-01-15 13:25 42D69CB1d01
-rw------- 1 DesktopUser DesktopUser   58691 2011-01-15 09:40 42EDEE51d01
-rw------- 1 DesktopUser DesktopUser  148011 2011-01-15 09:26 431B4BEAd01
-rw------- 1 DesktopUser DesktopUser   57098 2011-01-15 13:17 43E06119d01
-rw------- 1 DesktopUser DesktopUser   22231 2011-01-15 13:25 450959A7d01
-rw------- 1 DesktopUser DesktopUser   18506 2011-01-15 13:19 474DB75Fd01
-rw------- 1 DesktopUser DesktopUser   59077 2011-01-15 13:18 474FC0ADd01
-rw------- 1 DesktopUser DesktopUser   22200 2011-01-15 13:19 4A7FBAD9d01
-rw------- 1 DesktopUser DesktopUser   42160 2011-01-15 13:19 4A90759Cd01
-rw------- 1 DesktopUser DesktopUser   19842 2011-01-15 13:25 4B4D2748d01
-rw------- 1 DesktopUser DesktopUser   20574 2011-01-15 13:19 4DCF92BDd01
-rw------- 1 DesktopUser DesktopUser   26811 2011-01-15 13:19 4DEF9A6Cd01
-rw------- 1 DesktopUser DesktopUser   17690 2011-01-15 13:17 504043A6d01
-rw------- 1 DesktopUser DesktopUser   80447 2011-01-15 09:40 50955769d01
-rw------- 1 DesktopUser DesktopUser   19297 2011-01-15 13:17 53CF15D5d01
-rw------- 1 DesktopUser DesktopUser   23980 2011-01-15 13:25 53DCF93Ad01
-rw------- 1 DesktopUser DesktopUser   25326 2011-01-15 13:17 55F24B6Bd01
-rw------- 1 DesktopUser DesktopUser   20483 2011-01-15 13:24 56346737d01
-rw------- 1 DesktopUser DesktopUser   19913 2011-01-15 13:25 574089D4d01
-rw------- 1 DesktopUser DesktopUser   21686 2011-01-15 13:25 5832500Ed01
-rw------- 1 DesktopUser DesktopUser   19703 2011-01-15 13:17 583369DEd01
-rw------- 1 DesktopUser DesktopUser   38688 2011-01-15 13:20 5898C908d01
-rw------- 1 DesktopUser DesktopUser   30395 2011-01-15 09:26 58A65A13d01
-rw------- 1 DesktopUser DesktopUser   22210 2011-01-15 13:17 59E958F2d01
-rw------- 1 DesktopUser DesktopUser   23530 2011-01-15 13:25 5A80F9B5d01
-rw------- 1 DesktopUser DesktopUser   23042 2011-01-15 13:25 5AA74CBEd01
-rw------- 1 DesktopUser DesktopUser   18490 2011-01-15 13:25 5AEB624Cd01
-rw------- 1 DesktopUser DesktopUser   21350 2011-01-15 13:25 5AED1EB0d01
-rw------- 1 DesktopUser DesktopUser   59309 2011-01-15 13:25 5B891AA2d01
-rw------- 1 DesktopUser DesktopUser   22161 2011-01-15 13:25 5BDEF791d01
-rw------- 1 DesktopUser DesktopUser   35387 2011-01-15 08:38 5BFCA42Ad01
-rw------- 1 DesktopUser DesktopUser   16926 2011-01-15 13:19 5C00A335d01
-rw------- 1 DesktopUser DesktopUser   79547 2011-01-15 13:19 5C641A3Ed01
-rw------- 1 DesktopUser DesktopUser   17499 2011-01-15 13:15 5CC22546d01
-rw------- 1 DesktopUser DesktopUser   29018 2011-01-15 08:49 5D372ACCd01
-rw------- 1 DesktopUser DesktopUser   27372 2011-01-15 13:19 5DB93208d01
-rw------- 1 DesktopUser DesktopUser   57133 2011-01-15 13:25 5EE671C9d01
-rw------- 1 DesktopUser DesktopUser   52988 2011-01-15 13:25 5F052DFEd01
-rw------- 1 DesktopUser DesktopUser   20849 2011-01-15 13:24 5FB00806d01
-rw------- 1 DesktopUser DesktopUser   22346 2011-01-15 13:25 5FD0FC1Bd01
-rw------- 1 DesktopUser DesktopUser   22031 2011-01-15 13:25 5FEC1CDFd01
-rw------- 1 DesktopUser DesktopUser   22192 2011-01-15 13:25 60E23D3Ed01
-rw------- 1 DesktopUser DesktopUser   22074 2011-01-15 13:25 614A6372d01
-rw------- 1 DesktopUser DesktopUser   29571 2011-01-15 13:09 61E2478Fd01
-rw------- 1 DesktopUser DesktopUser   54347 2011-01-15 13:19 63487055d01
-rw------- 1 DesktopUser DesktopUser   33663 2011-01-15 13:20 645FFF1Ed01
-rw------- 1 DesktopUser DesktopUser   21264 2011-01-15 13:25 65DF887Dd01
-rw------- 1 DesktopUser DesktopUser   29837 2011-01-15 13:15 66024AE6d01
-rw------- 1 DesktopUser DesktopUser   48622 2011-01-15 09:26 6682E6D9d01
-rw------- 1 DesktopUser DesktopUser   22239 2011-01-15 13:24 67971834d01
-rw------- 1 DesktopUser DesktopUser   80360 2011-01-15 13:36 67E111DBd01
-rw------- 1 DesktopUser DesktopUser   18717 2011-01-15 13:28 6A8D1B67d01
-rw------- 1 DesktopUser DesktopUser   51181 2011-01-15 13:25 6A9830B6d01
-rw------- 1 DesktopUser DesktopUser   21720 2011-01-15 13:24 6B02B6DEd01
-rw------- 1 DesktopUser DesktopUser   34062 2011-01-15 09:19 6B06B8DFd01
-rw------- 1 DesktopUser DesktopUser   22387 2011-01-15 13:20 6B5780E8d01
-rw------- 1 DesktopUser DesktopUser   18905 2011-01-15 13:17 6BBA59DCd01
-rw------- 1 DesktopUser DesktopUser   28061 2011-01-15 09:04 6BCB3B8Bd01
-rw------- 1 DesktopUser DesktopUser   29619 2011-01-15 13:20 6BF8EEF3d01
-rw------- 1 DesktopUser DesktopUser   19850 2011-01-15 13:25 6C1860C6d01
-rw------- 1 DesktopUser DesktopUser   67011 2011-01-15 13:25 6CB5B602d01
-rw------- 1 DesktopUser DesktopUser   25366 2011-01-15 13:09 6CCD58DCd01
-rw------- 1 DesktopUser DesktopUser   26866 2011-01-15 13:09 6CE38658d01
-rw------- 1 DesktopUser DesktopUser   18884 2011-01-15 13:25 6FF87D4Dd01
-rw------- 1 DesktopUser DesktopUser  113063 2011-01-15 13:36 703416E7d01
-rw------- 1 DesktopUser DesktopUser   28749 2011-01-15 09:04 7062567Dd01
-rw------- 1 DesktopUser DesktopUser   18012 2011-01-15 13:17 710DE005d01
-rw------- 1 DesktopUser DesktopUser   86392 2011-01-15 13:30 73A25555d01
-rw------- 1 DesktopUser DesktopUser   22709 2011-01-15 13:24 73AEDBFBd01
-rw------- 1 DesktopUser DesktopUser   74840 2011-01-15 08:49 741C093Cd01
-rw------- 1 DesktopUser DesktopUser   21327 2011-01-15 13:25 74F5876Fd01
-rw------- 1 DesktopUser DesktopUser   21781 2011-01-15 13:24 75CF3F89d01
-rw------- 1 DesktopUser DesktopUser   40795 2011-01-15 13:20 76354385d01
-rw------- 1 DesktopUser DesktopUser   22386 2011-01-15 13:24 7684B957d01
-rw------- 1 DesktopUser DesktopUser   22255 2011-01-15 13:24 770B371Cd01
-rw------- 1 DesktopUser DesktopUser   16545 2011-01-15 13:25 784B079Ed01
-rw------- 1 DesktopUser DesktopUser   21519 2011-01-15 13:25 789030E4d01
-rw------- 1 DesktopUser DesktopUser   37263 2011-01-15 09:26 789634D3d01
-rw------- 1 DesktopUser DesktopUser   25523 2011-01-15 13:25 78CB12C3d01
-rw------- 1 DesktopUser DesktopUser   22634 2011-01-15 13:25 7AA48EBBd01
-rw------- 1 DesktopUser DesktopUser   20414 2011-01-15 13:25 7ABC1C8Dd01
-rw------- 1 DesktopUser DesktopUser   18143 2011-01-15 09:27 7ACBB7C3d01
-rw------- 1 DesktopUser DesktopUser   17502 2011-01-15 13:25 7D246C2Bd01
-rw------- 1 DesktopUser DesktopUser   19371 2011-01-15 13:25 7D8B88F9d01
-rw------- 1 DesktopUser DesktopUser   21337 2011-01-15 13:17 7DBCDF3Cd01
-rw------- 1 DesktopUser DesktopUser   26563 2011-01-15 13:19 7E04B1D9d01
-rw------- 1 DesktopUser DesktopUser   18646 2011-01-15 13:28 7E268F2Bd01
-rw------- 1 DesktopUser DesktopUser   19656 2011-01-15 13:28 7EF08CADd01
-rw------- 1 DesktopUser DesktopUser   61073 2011-01-15 13:16 7F6311E2d01
-rw------- 1 DesktopUser DesktopUser   21005 2011-01-15 13:25 7F837442d01
-rw------- 1 DesktopUser DesktopUser   20606 2011-01-15 13:25 7FC05675d01
-rw------- 1 DesktopUser DesktopUser   23040 2011-01-15 13:25 809D590Cd01
-rw------- 1 DesktopUser DesktopUser   55805 2011-01-15 09:27 80DA202Fd01
-rw------- 1 DesktopUser DesktopUser   16713 2011-01-15 13:17 81EEDE1Ed01
-rw------- 1 DesktopUser DesktopUser  147848 2011-01-15 13:36 822562EFd01
-rw------- 1 DesktopUser DesktopUser   61309 2011-01-15 13:16 83917506d01
-rw------- 1 DesktopUser DesktopUser   17215 2011-01-15 13:15 83C704CCd01
-rw------- 1 DesktopUser DesktopUser   19488 2011-01-15 13:17 84CD7111d01
-rw------- 1 DesktopUser DesktopUser   22239 2011-01-15 13:25 853218B3d01
-rw------- 1 DesktopUser DesktopUser   20646 2011-01-15 13:25 866C0CA2d01
-rw------- 1 DesktopUser DesktopUser   41058 2011-01-15 13:25 86CF6720d01
-rw------- 1 DesktopUser DesktopUser   71525 2011-01-15 13:18 882B7074d01
-rw------- 1 DesktopUser DesktopUser  101412 2011-01-15 09:41 88D80EB1d01
-rw------- 1 DesktopUser DesktopUser   23004 2011-01-15 09:27 88E6D21Ed01
-rw------- 1 DesktopUser DesktopUser   24819 2011-01-15 13:19 89165237d01
-rw------- 1 DesktopUser DesktopUser   16902 2011-01-15 09:40 893A5247d01
-rw------- 1 DesktopUser DesktopUser   21448 2011-01-15 13:24 8A0491FCd01
-rw------- 1 DesktopUser DesktopUser   24789 2011-01-15 09:27 8A74792Cd01
-rw------- 1 DesktopUser DesktopUser   21058 2011-01-15 13:24 8AF2B365d01
-rw------- 1 DesktopUser DesktopUser   24304 2011-01-15 13:19 8F1FF9ABd01
-rw------- 1 DesktopUser DesktopUser   18540 2011-01-15 13:25 8F33619Fd01
-rw------- 1 DesktopUser DesktopUser   20203 2011-01-15 13:25 8F3AE542d01
-rw------- 1 DesktopUser DesktopUser   19753 2011-01-15 13:24 8F665ACEd01
-rw------- 1 DesktopUser DesktopUser   45936 2011-01-15 13:24 8F9F4A8Bd01
-rw------- 1 DesktopUser DesktopUser   64640 2011-01-15 13:16 8FB4F392d01
-rw------- 1 DesktopUser DesktopUser   47873 2011-01-15 13:25 907F11A1d01
-rw------- 1 DesktopUser DesktopUser   17786 2011-01-15 08:38 91081CBFd01
-rw------- 1 DesktopUser DesktopUser   35517 2011-01-15 13:25 911D3FF0d01
-rw------- 1 DesktopUser DesktopUser   50039 2011-01-15 13:20 9254CA56d01
-rw------- 1 DesktopUser DesktopUser   22046 2011-01-15 13:15 9257CB8Fd01
-rw------- 1 DesktopUser DesktopUser   20891 2011-01-15 13:36 92CD5C8Dd01
-rw------- 1 DesktopUser DesktopUser   28700 2011-01-15 08:49 945703FDd01
-rw------- 1 DesktopUser DesktopUser   68281 2011-01-15 13:17 94B26850d01
-rw------- 1 DesktopUser DesktopUser   17136 2011-01-15 13:25 94CB6466d01
-rw------- 1 DesktopUser DesktopUser  112257 2011-01-15 13:34 94D8D34Bd01
-rw------- 1 DesktopUser DesktopUser   60599 2011-01-15 13:18 950456C7d01
-rw------- 1 DesktopUser DesktopUser   22269 2011-01-15 13:25 9609B458d01
-rw------- 1 DesktopUser DesktopUser   63656 2011-01-15 13:20 96C2E66Cd01
-rw------- 1 DesktopUser DesktopUser   23885 2011-01-15 08:49 978BDDA9d01
-rw------- 1 DesktopUser DesktopUser   44058 2011-01-15 13:20 97E55E17d01
-rw------- 1 DesktopUser DesktopUser   21068 2011-01-15 13:25 98213757d01
-rw------- 1 DesktopUser DesktopUser  113528 2011-01-15 13:29 99A394A8d01
-rw------- 1 DesktopUser DesktopUser   17350 2011-01-15 13:17 9A3C8781d01
-rw------- 1 DesktopUser DesktopUser   47473 2011-01-15 09:27 9B4A2DF5d01
-rw------- 1 DesktopUser DesktopUser   20002 2011-01-15 13:28 9BE84708d01
-rw------- 1 DesktopUser DesktopUser   21166 2011-01-15 09:25 9C5B265Ed01
-rw------- 1 DesktopUser DesktopUser   37390 2011-01-15 08:38 9D80B995d01
-rw------- 1 DesktopUser DesktopUser   58347 2011-01-15 13:25 9E4FA58Ed01
-rw------- 1 DesktopUser DesktopUser   26331 2011-01-15 13:25 A02A333Ed01
-rw------- 1 DesktopUser DesktopUser   19215 2011-01-15 13:19 A0A063F4d01
-rw------- 1 DesktopUser DesktopUser   24124 2011-01-15 13:24 A128942Ed01
-rw------- 1 DesktopUser DesktopUser   20890 2011-01-15 13:24 A182298Bd01
-rw------- 1 DesktopUser DesktopUser   64161 2011-01-15 13:24 A1DACE8Ad01
-rw------- 1 DesktopUser DesktopUser   24193 2011-01-15 13:25 A2313C33d01
-rw------- 1 DesktopUser DesktopUser   16397 2011-01-15 13:15 A3B265B0d01
-rw------- 1 DesktopUser DesktopUser   22707 2011-01-15 13:17 A42F018Ed01
-rw------- 1 DesktopUser DesktopUser   68524 2011-01-15 13:18 A495C8D2d01
-rw------- 1 DesktopUser DesktopUser   28736 2011-01-15 13:24 A535FCD0d01
-rw------- 1 DesktopUser DesktopUser   18450 2011-01-15 13:17 A55D17AFd01
-rw------- 1 DesktopUser DesktopUser   18457 2011-01-15 13:19 A5BB2EDBd01
-rw------- 1 DesktopUser DesktopUser   31049 2011-01-15 09:26 A68FCB6Ad01
-rw------- 1 DesktopUser DesktopUser   20143 2011-01-15 13:10 A73D018Fd01
-rw------- 1 DesktopUser DesktopUser   27540 2011-01-15 13:09 A7531EE3d01
-rw------- 1 DesktopUser DesktopUser   27550 2011-01-15 13:25 A765EDE4d01
-rw------- 1 DesktopUser DesktopUser   22719 2011-01-15 13:24 A7A23293d01
-rw------- 1 DesktopUser DesktopUser   20163 2011-01-15 13:25 A87E56C7d01
-rw------- 1 DesktopUser DesktopUser   17740 2011-01-15 13:17 A9752B66d01
-rw------- 1 DesktopUser DesktopUser   21174 2011-01-15 13:17 AB69473Dd01
-rw------- 1 DesktopUser DesktopUser   22740 2011-01-15 13:25 AC0C1A07d01
-rw------- 1 DesktopUser DesktopUser   16681 2011-01-15 13:24 ADB082CCd01
-rw------- 1 DesktopUser DesktopUser   64810 2011-01-15 13:16 ADCCF16Cd01
-rw------- 1 DesktopUser DesktopUser   22707 2011-01-15 09:26 AE8E9721d01
-rw------- 1 DesktopUser DesktopUser   22007 2011-01-15 13:25 AF10D35Ed01
-rw------- 1 DesktopUser DesktopUser   21915 2011-01-15 13:19 AF1EDDBFd01
-rw------- 1 DesktopUser DesktopUser   21178 2011-01-15 13:25 B31F7852d01
-rw------- 1 DesktopUser DesktopUser   17048 2011-01-15 13:19 B33D0B00d01
-rw------- 1 DesktopUser DesktopUser   26429 2011-01-15 13:09 B42A31B7d01
-rw------- 1 DesktopUser DesktopUser   20065 2011-01-15 13:25 B54ACA4Cd01
-rw------- 1 DesktopUser DesktopUser   33810 2011-01-15 13:24 B6C7869Bd01
-rw------- 1 DesktopUser DesktopUser   22098 2011-01-15 13:25 B74CDC2Dd01
-rw------- 1 DesktopUser DesktopUser   16704 2011-01-15 13:26 B88C0E3Ed01
-rw------- 1 DesktopUser DesktopUser   19638 2011-01-15 13:25 B8A56F29d01
-rw------- 1 DesktopUser DesktopUser   31656 2011-01-15 09:26 B910713Ad01
-rw------- 1 DesktopUser DesktopUser   69354 2011-01-15 13:17 B992103Fd01
-rw------- 1 DesktopUser DesktopUser   21031 2011-01-15 13:24 B9EB05D2d01
-rw------- 1 DesktopUser DesktopUser   71396 2011-01-15 13:19 BA55BFE2d01
-rw------- 1 DesktopUser DesktopUser   57459 2011-01-15 13:19 BA6432C8d01
-rw------- 1 DesktopUser DesktopUser   22314 2011-01-15 13:25 BBA07C6Dd01
-rw------- 1 DesktopUser DesktopUser  105046 2011-01-15 13:19 BBC530C3d01
-rw------- 1 DesktopUser DesktopUser   22378 2011-01-15 13:24 BC2F77FCd01
-rw------- 1 DesktopUser DesktopUser   20271 2011-01-15 13:25 BCBDDCB4d01
-rw------- 1 DesktopUser DesktopUser   84178 2011-01-15 13:16 BCFF4E05d01
-rw------- 1 DesktopUser DesktopUser   17164 2011-01-15 13:17 BE06BD8Ad01
-rw------- 1 DesktopUser DesktopUser   22201 2011-01-15 13:24 BE3BEFE9d01
-rw------- 1 DesktopUser DesktopUser   30641 2011-01-15 13:19 BE7611F6d01
-rw------- 1 DesktopUser DesktopUser   33222 2011-01-15 13:20 BF4A33BAd01
-rw------- 1 DesktopUser DesktopUser   63681 2011-01-15 13:16 C037497Dd01
-rw------- 1 DesktopUser DesktopUser  102744 2011-01-15 13:19 C103E737d01
-rw------- 1 DesktopUser DesktopUser  105044 2011-01-15 13:24 C1997A72d01
-rw------- 1 DesktopUser DesktopUser   21804 2011-01-15 13:25 C1A4769Ed01
-rw------- 1 DesktopUser DesktopUser   18509 2011-01-15 13:19 C221ACCFd01
-rw------- 1 DesktopUser DesktopUser   37015 2011-01-15 08:49 C3C03BEFd01
-rw------- 1 DesktopUser DesktopUser   17317 2011-01-15 13:28 C4B50F5Fd01
-rw------- 1 DesktopUser DesktopUser   51596 2011-01-15 13:25 C4FEFDEAd01
-rw------- 1 DesktopUser DesktopUser   20954 2011-01-15 13:24 C5DE39F5d01
-rw------- 1 DesktopUser DesktopUser   22323 2011-01-15 13:25 C7B893D5d01
-rw------- 1 DesktopUser DesktopUser   20248 2011-01-15 13:25 C9BF388Cd01
-rw------- 1 DesktopUser DesktopUser  112808 2011-01-15 13:16 C9C536D9d01
-rw------- 1 DesktopUser DesktopUser   41364 2011-01-15 13:24 C9F0CAEBd01
-rw------- 1 DesktopUser DesktopUser   18743 2011-01-15 13:24 CA1086B2d01
-rw------- 1 DesktopUser DesktopUser   22821 2011-01-15 13:25 CA26C27Ad01
-rw------- 1 DesktopUser DesktopUser  176871 2011-01-15 13:37 CA2D3EE0d01
-rw------- 1 DesktopUser DesktopUser   17958 2011-01-15 13:17 CA763CF4d01
-rw------- 1 DesktopUser DesktopUser   18639 2011-01-15 13:25 CAC700B4d01
-rw------- 1 DesktopUser DesktopUser 1525756 2011-01-15 13:38 _CACHE_001_
-rw------- 1 DesktopUser DesktopUser 1898664 2011-01-15 13:37 _CACHE_002_
-rw------- 1 DesktopUser DesktopUser 8162077 2011-01-15 13:37 _CACHE_003_
-rw------- 1 DesktopUser DesktopUser     276 2011-01-15 08:38 _CACHE_MAP_
-rw------- 1 DesktopUser DesktopUser   21593 2011-01-15 13:24 CDFC59C0d01
-rw------- 1 DesktopUser DesktopUser   21788 2011-01-15 13:25 CF84C499d01
-rw------- 1 DesktopUser DesktopUser   22715 2011-01-15 13:24 D13A8C8Dd01
-rw------- 1 DesktopUser DesktopUser   20976 2011-01-15 13:24 D228DC70d01
-rw------- 1 DesktopUser DesktopUser   19297 2011-01-15 13:19 D2623BC7d01
-rw------- 1 DesktopUser DesktopUser   50754 2011-01-15 13:25 D5C83506d01
-rw------- 1 DesktopUser DesktopUser   19186 2011-01-15 13:25 D69E2238d01
-rw------- 1 DesktopUser DesktopUser   39530 2011-01-15 13:24 D6E396C9d01
-rw------- 1 DesktopUser DesktopUser   16860 2011-01-15 13:25 D723B672d01
-rw------- 1 DesktopUser DesktopUser   21170 2011-01-15 13:25 D7EB6697d01
-rw------- 1 DesktopUser DesktopUser   21066 2011-01-15 08:49 D7FF2707d01
-rw------- 1 DesktopUser DesktopUser   20937 2011-01-15 13:25 D876291Ed01
-rw------- 1 DesktopUser DesktopUser   20721 2011-01-15 13:24 D93F21F0d01
-rw------- 1 DesktopUser DesktopUser   35345 2011-01-15 13:19 D9E0DA55d01
-rw------- 1 DesktopUser DesktopUser   35588 2011-01-15 13:19 DA3A4837d01
-rw------- 1 DesktopUser DesktopUser   23568 2011-01-15 13:25 DAD88D3Cd01
-rw------- 1 DesktopUser DesktopUser   18312 2011-01-15 13:17 DAD91A90d01
-rw------- 1 DesktopUser DesktopUser   29541 2011-01-15 09:26 DB5E1227d01
-rw------- 1 DesktopUser DesktopUser   70838 2011-01-15 13:16 DB93AC94d01
-rw------- 1 DesktopUser DesktopUser   27057 2011-01-15 13:25 DBBAE540d01
-rw------- 1 DesktopUser DesktopUser   22787 2011-01-15 13:19 DC847ECAd01
-rw------- 1 DesktopUser DesktopUser   73669 2011-01-15 13:27 DD03FBF8d01
-rw------- 1 DesktopUser DesktopUser   16900 2011-01-15 08:38 DD94E7F2d01
-rw------- 1 DesktopUser DesktopUser   21433 2011-01-15 13:17 DDB1026Dd01
-rw------- 1 DesktopUser DesktopUser   19133 2011-01-15 13:19 DF2B92F1d01
-rw------- 1 DesktopUser DesktopUser   24223 2011-01-15 13:25 DF7CAB2Ad01
-rw------- 1 DesktopUser DesktopUser  170106 2011-01-15 13:31 E03C70DBd01
-rw------- 1 DesktopUser DesktopUser   16525 2011-01-15 13:28 E55C4C79d01
-rw------- 1 DesktopUser DesktopUser   56575 2011-01-15 13:16 E7F64A3Bd01
-rw------- 1 DesktopUser DesktopUser   23257 2011-01-15 13:19 E89285DBd01
-rw------- 1 DesktopUser DesktopUser   55014 2011-01-15 13:19 E9A0F713d01
-rw------- 1 DesktopUser DesktopUser   19575 2011-01-15 13:19 EAD25134d01
-rw------- 1 DesktopUser DesktopUser   18367 2011-01-15 13:19 EB47D838d01
-rw------- 1 DesktopUser DesktopUser   20905 2011-01-15 13:25 EC3ED120d01
-rw------- 1 DesktopUser DesktopUser   93055 2011-01-15 09:26 EC651522d01
-rw------- 1 DesktopUser DesktopUser   19556 2011-01-15 13:25 ED425CDAd01
-rw------- 1 DesktopUser DesktopUser   20347 2011-01-15 13:15 EE572D64d01
-rw------- 1 DesktopUser DesktopUser   19029 2011-01-15 13:25 EE728EDBd01
-rw------- 1 DesktopUser DesktopUser   99634 2011-01-15 13:25 EFBD94A9d01
-rw------- 1 DesktopUser DesktopUser   40418 2011-01-15 09:41 F076940Ed01
-rw------- 1 DesktopUser DesktopUser   17459 2011-01-15 13:09 F1109B7Bd01
-rw------- 1 DesktopUser DesktopUser   16710 2011-01-15 08:38 F17BC44Dd01
-rw------- 1 DesktopUser DesktopUser   21171 2011-01-15 13:25 F20CC592d01
-rw------- 1 DesktopUser DesktopUser   21737 2011-01-15 13:25 F35E9E70d01
-rw------- 1 DesktopUser DesktopUser   22133 2011-01-15 13:25 F48A719Fd01
-rw------- 1 DesktopUser DesktopUser   16777 2011-01-15 13:25 F52C64D0d01
-rw------- 1 DesktopUser DesktopUser   39880 2011-01-15 13:27 F55CDEECd01
-rw------- 1 DesktopUser DesktopUser   19550 2011-01-15 13:20 F77735E6d01
-rw------- 1 DesktopUser DesktopUser   22504 2011-01-15 13:19 FA71A827d01
-rw------- 1 DesktopUser DesktopUser  105539 2011-01-15 09:19 FADCC682d01
-rw------- 1 DesktopUser DesktopUser   61621 2011-01-15 13:25 FB0A0B7Fd01
-rw------- 1 DesktopUser DesktopUser   37013 2011-01-15 13:18 FB772DB3d01
-rw------- 1 DesktopUser DesktopUser  112302 2011-01-15 13:16 FD48F654d01
-rw------- 1 DesktopUser DesktopUser   21780 2011-01-15 13:24 FE3ABA67d01
-rw------- 1 DesktopUser DesktopUser   55087 2011-01-15 13:30 FE481DACd01
-rw------- 1 DesktopUser DesktopUser   21438 2011-01-15 13:25 FE597FE6d01
-rw------- 1 DesktopUser DesktopUser  113746 2011-01-15 13:31 FEBCB7EBd01
-rw------- 1 DesktopUser DesktopUser   16826 2011-01-15 13:17 FF8FFEDCd01

./firefox/bc3huk63.default/chrome:
total 8
-rw-r--r-- 1 DesktopUser DesktopUser 959 2010-08-11 21:11 userChrome-example.css
-rw-r--r-- 1 DesktopUser DesktopUser 663 2010-08-11 21:11 userContent-example.css

./firefox/bc3huk63.default/extensions:
total 8
drwxr-xr-x 6 DesktopUser DesktopUser 4096 2010-12-12 09:16 {c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}
drwxr-xr-x 7 DesktopUser DesktopUser 4096 2010-12-30 10:54 {d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}

./firefox/bc3huk63.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}:
total 24
drwxr-xr-x 2 DesktopUser DesktopUser 4096 2010-12-12 09:16 chrome
-rw-r--r-- 1 DesktopUser DesktopUser  230 2009-03-31 14:43 chrome.manifest
drwxr-xr-x 2 DesktopUser DesktopUser 4096 2010-12-12 09:16 content
drwxr-xr-x 3 DesktopUser DesktopUser 4096 2010-12-12 09:16 defaults
-rw-r--r-- 1 DesktopUser DesktopUser 1115 2010-12-10 20:11 install.rdf
drwxr-xr-x 2 DesktopUser DesktopUser 4096 2010-12-12 09:16 skin

./firefox/bc3huk63.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}/chrome:
total 0

./firefox/bc3huk63.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}/content:
total 44
-rw-r--r-- 1 DesktopUser DesktopUser 11371 2010-12-10 20:08 downloadyoutubevideosasmp.js
-rw-r--r-- 1 DesktopUser DesktopUser  1386 2009-06-14 09:55 options.xul
-rw-r--r-- 1 DesktopUser DesktopUser  2691 2019-09-25 22:40 prefman.js
-rw-r--r-- 1 DesktopUser DesktopUser 15161 2010-11-22 14:46 script-compiler.js
-rw-r--r-- 1 DesktopUser DesktopUser   454 2019-09-25 22:40 script-compiler-overlay.xul
-rw-r--r-- 1 DesktopUser DesktopUser  3454 2019-09-25 22:40 xmlhttprequester.js

./firefox/bc3huk63.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}/defaults:
total 4
drwxr-xr-x 2 DesktopUser DesktopUser 4096 2010-12-12 09:16 preferences

./firefox/bc3huk63.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}/defaults/preferences:
total 4
-rw-r--r-- 1 DesktopUser DesktopUser 63 2009-06-13 10:49 defaults.js

./firefox/bc3huk63.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}/skin:
total 4
-rw-r--r-- 1 DesktopUser DesktopUser 2826 2009-04-22 12:01 youtube.png

./firefox/bc3huk63.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}:
total 52
drwxr-xr-x 2 DesktopUser DesktopUser  4096 2010-12-30 10:54 chrome
-rw-r--r-- 1 DesktopUser DesktopUser  5090 2010-12-23 16:06 chrome.manifest
drwxr-xr-x 2 DesktopUser DesktopUser  4096 2010-12-30 10:54 components
drwxr-xr-x 3 DesktopUser DesktopUser  4096 2010-12-30 10:54 defaults
-rw-r--r-- 1 DesktopUser DesktopUser   708 2010-12-23 16:06 icon.png
-rw-r--r-- 1 DesktopUser DesktopUser 18200 2010-12-23 16:06 install.rdf
drwxr-xr-x 2 DesktopUser DesktopUser  4096 2010-12-30 10:54 META-INF
drwxr-xr-x 2 DesktopUser DesktopUser  4096 2010-12-30 10:54 modules

./firefox/bc3huk63.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/chrome:
total 1456
-rw-r--r-- 1 DesktopUser DesktopUser 1489925 2010-12-23 16:06 adblockplus.jar

./firefox/bc3huk63.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/components:
total 4
-rw-r--r-- 1 DesktopUser DesktopUser 3841 2010-12-23 16:06 Initializer.js

./firefox/bc3huk63.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/defaults:
total 8
-rw-r--r-- 1 DesktopUser DesktopUser  137 2010-12-23 16:06 patterns.ini
drwxr-xr-x 2 DesktopUser DesktopUser 4096 2010-12-30 10:54 preferences

./firefox/bc3huk63.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/defaults/preferences:
total 4
-rw-r--r-- 1 DesktopUser DesktopUser 2209 2010-12-23 16:06 adblockplus.js

./firefox/bc3huk63.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/META-INF:
total 16
-rw-r--r-- 1 DesktopUser DesktopUser 3287 2010-12-23 16:06 manifest.mf
-rw-r--r-- 1 DesktopUser DesktopUser 4507 2010-12-23 16:06 zigbert.rsa
-rw-r--r-- 1 DesktopUser DesktopUser 3395 2010-12-23 16:06 zigbert.sf

./firefox/bc3huk63.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/modules:
total 240
-rw-r--r-- 1 DesktopUser DesktopUser  8080 2010-12-23 16:06 AppIntegrationFennec.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 37875 2010-12-23 16:06 AppIntegration.jsm
-rw-r--r-- 1 DesktopUser DesktopUser  6083 2010-12-23 16:06 Bootstrap.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 17897 2010-12-23 16:06 ContentPolicy.jsm
-rw-r--r-- 1 DesktopUser DesktopUser  7756 2010-12-23 16:06 ElemHide.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 20916 2010-12-23 16:06 FilterClasses.jsm
-rw-r--r-- 1 DesktopUser DesktopUser  5535 2010-12-23 16:06 FilterListener.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 19984 2010-12-23 16:06 FilterStorage.jsm
-rw-r--r-- 1 DesktopUser DesktopUser  9000 2010-12-23 16:06 Matcher.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 14882 2010-12-23 16:06 ObjectTabs.jsm
-rw-r--r-- 1 DesktopUser DesktopUser  7328 2010-12-23 16:06 Prefs.jsm
-rw-r--r-- 1 DesktopUser DesktopUser  5562 2010-12-23 16:06 Public.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 10647 2010-12-23 16:06 RequestNotifier.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 11571 2010-12-23 16:06 SubscriptionClasses.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 17633 2010-12-23 16:06 Synchronizer.jsm
-rw-r--r-- 1 DesktopUser DesktopUser 13915 2010-12-23 16:06 Utils.jsm

./firefox/bc3huk63.default/minidumps:
total 0

./firefox/bc3huk63.default/OfflineCache:
total 12
-rw-r--r-- 1 DesktopUser DesktopUser 10240 2010-12-17 00:07 index.sqlite

./firefox/Crash Reports:
total 36
-rw-r--r-- 1 DesktopUser DesktopUser   55 2010-09-26 21:41 crashreporter.ini
-rw------- 1 DesktopUser DesktopUser   10 2010-09-10 11:03 InstallTime20100825160138
-rw------- 1 DesktopUser DesktopUser   10 2010-09-18 15:23 InstallTime20100915180648
-rw------- 1 DesktopUser DesktopUser   10 2010-10-12 21:00 InstallTime20100922075949
-rw------- 1 DesktopUser DesktopUser   10 2010-10-21 11:13 InstallTime20101013125417
-rw------- 1 DesktopUser DesktopUser   10 2010-10-28 15:34 InstallTime20101027124735
-rw------- 1 DesktopUser DesktopUser   10 2010-12-09 20:42 InstallTime20101206121716
-rw------- 1 DesktopUser DesktopUser   10 2010-09-26 21:41 LastCrash
drwx------ 2 DesktopUser DesktopUser 4096 2010-09-26 21:41 pending
-rw-r--r-- 1 DesktopUser DesktopUser    0 2010-09-26 21:41 submit.log

./firefox/Crash Reports/pending:
total 0

```

I'm pretty sure it's not firefox doing it. It appears that sshfs is the culprit. And it really was happening.

---

### Post by bilkay on 2011-01-16
I'm finding files erroneously owned by root in other directories that mount via autofs and sshfs. 

/etc/auto.master:
```
/userdirs       /etc/auto.ssh  -v --ghost --timeout=10
```/etc/auto.ssh:
```
#typical line:
user.mozilla -fstype=fuse,port=12023,rw,nodev,nonempty,noatime,allow_other,max_read=65536 :sshfs\#Server:\/home/user/.mozilla
```

---

### Post by uRock on 2011-01-16
Have you installed any .debs or any other downloaded softwares? I am starting to wonder if you have installed something that does more than it is supposed to do.

---

