---
title: "apt-get update problems"
date: 2011-09-19
forum: Server Platforms
---

### Post by JAZ1976 on 2011-09-19
Hey everyone,

Just set up a new Ubuntu Server 11.04 at my company and I am having trouble installing software. Every time I do sudo apt-get update this is what I am getting. Can anyone help me please.

```
itadmin@LINUXSVR01:/$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages/DiffIndex
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages/DiffIndex
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages/DiffIndex
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages/DiffIndex
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages/DiffIndex
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages/DiffIndex
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages/DiffIndex
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages/DiffIndex
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages
15% [19 Packages bzip2 0 B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages
20% [20 Packages bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages
23% [21 Packages bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages
27% [22 Packages bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
30% [23 Translation-en_US bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
33% [24 Translation-en bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
36% [25 Translation-en_US bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
38% [26 Translation-en bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
40% [27 Translation-en_US bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
42% [28 Translation-en bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
44% [29 Translation-en_US bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
46% [30 Translation-en bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages
48% [31 Packages bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages
49% [32 Packages bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages
51% [33 Packages bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages
52% [34 Packages bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
54% [35 Translation-en_US bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
55% [36 Translation-en bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
56% [37 Translation-en_US bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
57% [38 Translation-en bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
58% [39 Translation-en_US bzip2 0 B] [Connecting to 192.168.20.251 (192.168.20.bzip2: (stdin) is not a bzip2 file.
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
59% [40 Translation-en bzip2 0 B] [Connecting to 192.168.20.251 (192.168.20.251bzip2: (stdin) is not a bzip2 file.
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
60% [41 Translation-en_US bzip2 0 B] [Connecting to 192.168.20.251 (192.168.20.bzip2: (stdin) is not a bzip2 file.
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
61% [42 Translation-en bzip2 0 B] [Connecting to 192.168.20.251 (192.168.20.251bzip2: (stdin) is not a bzip2 file.
61% [19 Packages xz 0 B] [Connecting to us.archive.ubuntu.com (91.189.92.170)]/usr/bin/xz: (stdin): File format not recognized
61% [20 Packages xz 0 B] [Connecting to 192.168.20.251 (192.168.20.251)]/usr/bin/xz: (stdin): File format not recognized
61% [21 Packages xz 0 B] [Connecting to 192.168.20.251 (192.168.20.251)]/usr/bin/xz: (stdin): File format not recognized
61% [22 Packages xz 0 B]/usr/bin/xz: (stdin): File format not recognized
61% [23 Translation-en_US xz 0 B]/usr/bin/xz: (stdin): File format not recognized
61% [24 Translation-en xz 0 B]/usr/bin/xz: (stdin): File format not recognized
61% [25 Translation-en_US xz 0 B]/usr/bin/xz: (stdin): File format not recognized
61% [26 Translation-en xz 0 B]/usr/bin/xz: (stdin): File format not recognized
61% [27 Translation-en_US xz 0 B]/usr/bin/xz: (stdin): File format not recognized
61% [28 Translation-en xz 0 B]/usr/bin/xz: (stdin): File format not recognized
61% [29 Translation-en_US xz 0 B]/usr/bin/xz: (stdin): File format not recognized
61% [30 Translation-en xz 0 B]                                     5,993 B/s 3s/usr/bin/xz: (stdin): File format not recognized
61% [31 Packages xz 0 B]                                           5,993 B/s 3s/usr/bin/xz: (stdin): File format not recognized
61% [32 Packages xz 0 B]                                           5,993 B/s 3s/usr/bin/xz: (stdin): File format not recognized
61% [33 Packages xz 0 B]                                           5,993 B/s 3s/usr/bin/xz: (stdin): File format not recognized
61% [34 Packages xz 0 B]                                           5,993 B/s 3s/usr/bin/xz: (stdin): File format not recognized
61% [35 Translation-en_US xz 0 B]                                  5,993 B/s 3s/usr/bin/xz: (stdin): File format not recognized
61% [36 Translation-en xz 0 B]                                     5,993 B/s 3s/usr/bin/xz: (stdin): File format not recognized
61% [37 Translation-en_US xz 0 B] [Connecting to 192.168.20.251 (192.168.20.251/usr/bin/xz: (stdin): File format not recognized
61% [38 Translation-en xz 0 B] [Connecting to 192.168.20.251 (192.168.20.251)]/usr/bin/xz: (stdin): File format not recognized
61% [39 Translation-en_US xz 0 B]                                  5,993 B/s 3s/usr/bin/xz: (stdin): File format not recognized
61% [40 Translation-en xz 0 B]                                     5,993 B/s 3s/usr/bin/xz: (stdin): File format not recognized
61% [41 Translation-en_US xz 0 B]                                  5,993 B/s 3s/usr/bin/xz: (stdin): File format not recognized
61% [42 Translation-en xz 0 B]                                     5,993 B/s 3s/usr/bin/xz: (stdin): File format not recognized
Fetched 60.4 kB in 9s (6,199 B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
itadmin@LINUXSVR01:/$
```

---

### Post by Rubi1200 on 2011-09-19
Hi and welcome to the forums :)

Try these commands in the terminal (copy/paste for best results):
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```
The first command removes corrupted package lists, the second refreshes them.

---

### Post by JAZ1976 on 2011-09-20
Rubi,

Thank you for replying to my post. I tried your suggestion and this is what I get. 

```
itadmin@LINUXSVR01:/$ sudo rm /var/lib/apt/lists/* -vf
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_restricted_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_universe_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_main_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_i18n_Translation-en%5fUS'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty-updates_universe_i18n_Translation-en%5fUS'
itadmin@LINUXSVR01:/$


itadmin@LINUXSVR01:/$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main amd64 Packages
99% [3 Packages bzip2 0 B] [Connecting to us.archive.ubuntu.com]bzip2: (stdin) is not a bzip2 file.
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted amd64 Packages
99% [4 Packages bzip2 0 B] [Connecting to 192.168.20.251 (192.168.20.251)]bzip2: (stdin) is not a bzip2 file.
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe amd64 Packages
99% [5 Packages bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse amd64 Packages
99% [6 Packages bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main amd64 Packages
63% [11 Packages bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted amd64 Packages
66% [12 Packages bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe amd64 Packages
69% [13 Packages bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse amd64 Packages
71% [14 Packages bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
55% [3 Packages xz 0 B] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
55% [4 Packages xz 0 B] [Connecting to 192.168.20.251 (192.168.20.251)]/usr/bin/xz: (stdin): File format not recognized
55% [5 Packages xz 0 B] [Waiting for headers]/usr/bin/xz: (stdin): File format not recognized
55% [6 Packages xz 0 B] [Connecting to 192.168.20.251 (192.168.20.251)]/usr/bin/xz: (stdin): File format not recognized
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
57% [19 Translation-en_US bzip2 0 B] [Connecting to us.archive.ubuntu.com]bzip2: (stdin) is not a bzip2 file.
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en
59% [20 Translation-en bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US
61% [21 Translation-en_US bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en
63% [22 Translation-en bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US
65% [23 Translation-en_US bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en
66% [24 Translation-en bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US
67% [25 Translation-en_US bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en
69% [26 Translation-en bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
69% [11 Packages xz 0 B]/usr/bin/xz: (stdin): File format not recognized
69% [12 Packages xz 0 B]/usr/bin/xz: (stdin): File format not recognized
69% [13 Packages xz 0 B]/usr/bin/xz: (stdin): File format not recognized
69% [14 Packages xz 0 B]/usr/bin/xz: (stdin): File format not recognized
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US
70% [27 Translation-en_US bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en
71% [28 Translation-en bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US
72% [29 Translation-en_US bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en
73% [30 Translation-en bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US
74% [31 Translation-en_US bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en
74% [32 Translation-en bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US
75% [33 Translation-en_US bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en
76% [34 Translation-en bzip2 0 B]bzip2: (stdin) is not a bzip2 file.
76% [19 Translation-en_US xz 0 B]/usr/bin/xz: (stdin): File format not recognized
76% [20 Translation-en xz 0 B]/usr/bin/xz: (stdin): File format not recognized
76% [21 Translation-en_US xz 0 B]/usr/bin/xz: (stdin): File format not recognized
76% [22 Translation-en xz 0 B]/usr/bin/xz: (stdin): File format not recognized
76% [23 Translation-en_US xz 0 B]/usr/bin/xz: (stdin): File format not recognized
76% [24 Translation-en xz 0 B]/usr/bin/xz: (stdin): File format not recognized
76% [25 Translation-en_US xz 0 B]/usr/bin/xz: (stdin): File format not recognized
76% [26 Translation-en xz 0 B]                                     5,797 B/s 1s/usr/bin/xz: (stdin): File format not recognized
76% [27 Translation-en_US xz 0 B]                                  5,797 B/s 1s/usr/bin/xz: (stdin): File format not recognized
76% [28 Translation-en xz 0 B]                                     5,797 B/s 1s/usr/bin/xz: (stdin): File format not recognized
76% [29 Translation-en_US xz 0 B]                                  5,797 B/s 1s/usr/bin/xz: (stdin): File format not recognized
76% [30 Translation-en xz 0 B]                                     5,797 B/s 1s/usr/bin/xz: (stdin): File format not recognized
76% [31 Translation-en_US xz 0 B]                                  5,797 B/s 1s/usr/bin/xz: (stdin): File format not recognized
76% [32 Translation-en xz 0 B]                                     5,797 B/s 1s/usr/bin/xz: (stdin): File format not recognized
76% [33 Translation-en_US xz 0 B]                                  5,797 B/s 1s/usr/bin/xz: (stdin): File format not recognized
76% [34 Translation-en xz 0 B]                                     5,797 B/s 1s/usr/bin/xz: (stdin): File format not recognized
Fetched 48.9 kB in 9s (5,357 B/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
itadmin@LINUXSVR01:/$
```

---

### Post by oldos2er on 2011-09-20
Is this machine connected to the internet?

---

### Post by JAZ1976 on 2011-09-20
I assume so oldos2er, I can ping websites outside of my network. I just pinged google to test it. Is there another way to make sure?

---

### Post by DRouleau on 2011-09-20
> **oldos2er said:**
> Is this machine connected to the internet?

Also check DNS, I had the same problem when I first set mine up... fat fingered my DNS and had .98 instead of .99

---

### Post by JAZ1976 on 2011-09-20
DRouleau,
The DNS servers in resolv.conf are right. Here is the output.

itadmin@LINUXSVR01:/etc$ more resolv.conf
search national-lumber.com
nameserver 192.168.20.203
nameserver 192.168.20.193
itadmin@LINUXSVR01:/etc$

Do I need to change nameserver to the name of the server?

---

### Post by JAZ1976 on 2011-09-21
Could it be that this is a virtual server hosted on a Hype-V server? The ubuntu server was set up by my network admin, but I am the one who will be administering the ubuntu server.

---

### Post by SecretCode on 2011-09-21
It might be worth changing the update server - [COLOR="Silver"]in Synaptic Package Manager: Settings > Repositories > change the 'Download from:' dropdown to another location.[/COLOR] Sorry it's a server ... make the change in /etc/apt/sources.list

If you have any kind of caching between your server and the net, like apt-cacher-ng, you should look at clearing the erroring files out of that cache.

---

### Post by JAZ1976 on 2011-09-21
Where can I get a list of sources to put into the sources.list file?

---

### Post by koenn on 2011-09-21
> **SecretCode said:**
> It might be worth changing the update server -  in /etc/apt/sources.list

If you have any kind of caching between your server and the net, like apt-cacher-ng, you should look at clearing the erroring files out of that cache.

+1 
I've seen similar errors when going through apt-proxy or even plain squid.
not sure if it was caused by the caching or by the backend servers, so both of SecretCode's suggestions make sense. 

try without proxy if that's an option, or clean out the proxy cache, or try with different mirrors


here's a list - unfortunately, you'll have to work their URL's into the suitable sources.listr format yourself, but that is not very hard.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

---

### Post by SecretCode on 2011-09-21
Looks like your current main server is [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) - do a global change of that to [http://archive.ubuntu.com/](http://archive.ubuntu.com/) or [http://mirrors.us.kernel.org/](http://mirrors.us.kernel.org/) or any other.

---

### Post by JAZ1976 on 2011-09-23
SecretCode,

I changed the sources.list from [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) to [http://archive.ubuntu.com/](http://archive.ubuntu.com/) and I am getting the same results.

Here is the output.

```
itadmin@(none):/$ sudo apt-get update > update_log.txt
-bash: update_log.txt: Permission denied
itadmin@(none):/$ sudo apt-get update > update_log
-bash: update_log: Permission denied
itadmin@(none):/$ sudo apt-get update | tee file.txt
sudo: unable to resolve host (none)
tee: file.txt: Permission denied
[sudo] password for itadmin:
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources/DiffIndex
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources/DiffIndex
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources/DiffIndex
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Sources/DiffIndex
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Sources/DiffIndex
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main amd64 Packages/DiffIndex
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted amd64 Packages/DiffIndex
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe amd64 Packages/DiffIndex
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse amd64 Packages/DiffIndex
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse TranslationIndex
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted TranslationIndex
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources/DiffIndex
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources/DiffIndex
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources/DiffIndex
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages/DiffIndex
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages/DiffIndex
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages/DiffIndex
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages/DiffIndex
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe TranslationIndex
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Sources/DiffIndex
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Sources/DiffIndex
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Sources/DiffIndex
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources
bzip2: (stdin) is not a bzip2 file.
bzip2: (stdin) is not a bzip2 file.
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Sources/DiffIndex
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources
bzip2: (stdin) is not a bzip2 file.
Get:35 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main amd64 Packages/DiffIndex
Get:36 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources
bzip2: (stdin) is not a bzip2 file.
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted amd64 Packages/DiffIndex
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe amd64 Packages/DiffIndex
Get:40 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse amd64 Packages/DiffIndex
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main TranslationIndex
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:45 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:46 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Get:47 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted TranslationIndex
Get:48 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe TranslationIndex
Get:49 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources
bzip2: (stdin) is not a bzip2 file.
Get:50 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources
bzip2: (stdin) is not a bzip2 file.
Get:51 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Sources
bzip2: (stdin) is not a bzip2 file.
Get:52 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Sources
bzip2: (stdin) is not a bzip2 file.
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:56 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:57 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:58 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:59 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:60 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:61 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:62 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
bzip2: (stdin) is not a bzip2 file.
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
Get:63 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:64 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:65 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:66 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:67 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:68 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:69 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:70 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:71 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:72 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Sources
bzip2: (stdin) is not a bzip2 file.
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
Get:73 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Sources
bzip2: (stdin) is not a bzip2 file.
Get:74 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Sources
bzip2: (stdin) is not a bzip2 file.
Get:75 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Sources
bzip2: (stdin) is not a bzip2 file.
Get:76 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:77 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:78 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:79 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:80 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:81 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:82 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en_US
bzip2: (stdin) is not a bzip2 file.
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
Get:83 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:84 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:85 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:86 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:87 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en
bzip2: (stdin) is not a bzip2 file.
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
Fetched 125 kB in 13s (9,234 B/s)
Reading package lists...
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
```

---

### Post by SecretCode on 2011-09-23
Hmm ...

Try
```
sudo apt-get clean
```
and then rerun the commands

---

### Post by JAZ1976 on 2011-09-23
After running sudo apt-get clean I ran sudo apt-get update and this is what I get.

```
itadmin@(none):~$ sudo apt-get update | tee file.txt
sudo: unable to resolve host (none)
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources/DiffIndex
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources/DiffIndex
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources/DiffIndex
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources/DiffIndex
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources/DiffIndex
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages/DiffIndex
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages/DiffIndex
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages/DiffIndex
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages/DiffIndex
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources/DiffIndex
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Sources/DiffIndex
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Sources/DiffIndex
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main amd64 Packages/DiffIndex
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted amd64 Packages/DiffIndex
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe amd64 Packages/DiffIndex
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse amd64 Packages/DiffIndex
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse TranslationIndex
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted TranslationIndex
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources
bzip2: (stdin) is not a bzip2 file.
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources
bzip2: (stdin) is not a bzip2 file.
bzip2: (stdin) is not a bzip2 file.
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources
bzip2: (stdin) is not a bzip2 file.
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:32 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:35 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:36 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe TranslationIndex
Get:37 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Sources/DiffIndex
Get:38 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Sources/DiffIndex
Get:39 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Sources/DiffIndex
Get:40 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Sources/DiffIndex
Get:41 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main amd64 Packages/DiffIndex
Get:42 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted amd64 Packages/DiffIndex
Get:43 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe amd64 Packages/DiffIndex
Get:44 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse amd64 Packages/DiffIndex
Get:45 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main TranslationIndex
Get:46 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:48 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:49 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:50 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:51 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:52 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
bzip2: (stdin) is not a bzip2 file.
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
Get:53 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Get:54 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted TranslationIndex
Get:55 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe TranslationIndex
Get:56 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources
bzip2: (stdin) is not a bzip2 file.
Get:57 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources
bzip2: (stdin) is not a bzip2 file.
Get:58 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Sources
bzip2: (stdin) is not a bzip2 file.
Get:59 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Sources
bzip2: (stdin) is not a bzip2 file.
Get:60 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:61 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:62 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe amd64 Packages
bzip2: (stdin) is not a bzip2 file.
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
Get:63 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:64 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:65 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:66 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:67 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:68 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:69 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:70 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:71 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:72 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Sources
bzip2: (stdin) is not a bzip2 file.
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
Get:73 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Sources
bzip2: (stdin) is not a bzip2 file.
Get:74 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Sources
bzip2: (stdin) is not a bzip2 file.
Get:75 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Sources
bzip2: (stdin) is not a bzip2 file.
Get:76 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:77 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:78 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:79 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse amd64 Packages
bzip2: (stdin) is not a bzip2 file.
Get:80 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:81 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:82 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:83 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:84 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:85 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en
bzip2: (stdin) is not a bzip2 file.
Get:86 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en_US
bzip2: (stdin) is not a bzip2 file.
Get:87 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en
bzip2: (stdin) is not a bzip2 file.
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
/usr/bin/xz: (stdin): File format not recognized
Fetched 125 kB in 13s (9,428 B/s)
Reading package lists...
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
itadmin@(none):~$
```

---

### Post by SecretCode on 2011-09-23
Well, I'm beyond puzzled now. I only have random suggestions left.

Can you move the server to a different site and try with a completely different network path? (Different firewalls, proxies, routers, even different ISP) - I suspect something corrupted is cached somewhere along the way.

Or else repeat the install elsewhere?

---

### Post by JAZ1976 on 2011-09-23
Ok, thank you for your help SecretCode, I'll see what I can do from here.

---

### Post by CharlesA on 2011-09-23
Try a different mirror.

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Also, please post long output in [noparse]```

```[/noparse] tags

---

### Post by JAZ1976 on 2011-10-03
Everyone,

I found out what was causing the problem. My companies firewall was asking for a username and password. To put the username and password in you have to go through a web browser. We ended up putting an exception for the server within the firewall. Sorry for the inconvenience, and thanks for the help. I do appreciate it.

---

### Post by Rubi1200 on 2011-10-03
Glad you managed to figure out the solution and that everything is normal again.

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy :)

---

### Post by tburnett80 on 2013-02-01
I was having the same issue, and changing from us.archive to just archive fixed my issue. Thanks guys.

---

