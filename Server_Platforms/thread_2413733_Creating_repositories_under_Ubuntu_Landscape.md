---
title: "Creating repositories under Ubuntu Landscape"
date: 2019-03-01
forum: Server Platforms
---

### Post by james.w.krych on 2019-03-01
[COLOR=#242729][FONT=Arial]I am just getting started with using Ubuntu Landscape. The plan is to use the quickstart version to gain experience with managing Ubuntu servers, 16 and 18, and to also create an on-site repository to limit traffic over the Internet from each asset.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]We are currently using Landscape On Premise release 19.01.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I am going to list the steps I believe are to be correct for our Ubuntu 18, bionic, servers.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]landscape-api create-distribution ubuntu[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]landscape-api create-series --pockets release,security,updates --components main,extras,restricted --architectures i386,amd64 --gpg-key secret-key --mirror-uri [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) --mirror-series bionic bionic ubuntu[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]landscape-api sync-mirror-pocket release bionic ubuntu 
landscape-api sync-mirror-pocket security bionic ubuntu 
landscape-api sync-mirror-pocket updates bionic ubuntu[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What else do I need to do after these commands? What needs to be corrected?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Very respectfully,[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]James[/FONT][/COLOR]

---

### Post by james.w.krych on 2019-03-01
Okay, with help from Ask Ubuntu, I have these steps and currently, the first sync is taking place.

[LEFT][FONT=Arial, sans-serif]**export LANDSCAPE_API_URI="https://landscapetest/api/"**[/FONT][/LEFT][FONT=Arial, sans-serif]**export LANDSCAPE_API_KEY="key"**[/FONT]
[FONT=Arial, sans-serif]**export LANDSCAPE_API_SECRET="longsecretkey"**[/FONT][LEFT]

[FONT=Arial, sans-serif]apt-get install rng-tools && sudo rngd -r /dev/urandom[/FONT][FONT=Arial, sans-serif]gpg &#8211;gen-key[/FONT][FONT=Arial, sans-serif]gpg -K[/FONT]
[FONT=Arial, sans-serif]gpg -a --export-secret-keys keyinfo > mirror-key.asc[/FONT]
[FONT=Arial, sans-serif]landscape-api import-gpg-key mirror-key mirror-key.asc[/FONT]
[/LEFT][COLOR=#242729][FONT=Arial, sans-serif]landscape-api create-distribution ubuntu[/FONT][/COLOR]

[COLOR=#111111][FONT=monospace, monospace]landscape-api create-series [COLOR=#183691]\[/COLOR][/FONT][/COLOR]
[COLOR=#111111]  [FONT=monospace, monospace]--pockets release,updates,security [/FONT][COLOR=#183691][FONT=monospace, monospace]\[/FONT][/COLOR][/COLOR]
[COLOR=#111111]  [FONT=monospace, monospace]--components main,restricted,universe,multiverse [/FONT][COLOR=#183691][FONT=monospace, monospace]\[/FONT][/COLOR][/COLOR]
[COLOR=#111111]  [FONT=monospace, monospace]--architectures amd64,i386 [/FONT][COLOR=#183691][FONT=monospace, monospace]\[/FONT][/COLOR][/COLOR]
[COLOR=#111111]  [FONT=monospace, monospace]--gpg-key mirror-key [/FONT][COLOR=#183691][FONT=monospace, monospace]\[/FONT][/COLOR][/COLOR]
[COLOR=#111111]  [FONT=monospace, monospace]--mirror-uri [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) [/FONT][COLOR=#183691][FONT=monospace, monospace]\[/FONT][/COLOR][/COLOR]
[COLOR=#111111]  [FONT=monospace, monospace]--mirror-series bionic bionic ubuntu[/FONT][/COLOR][h=2][COLOR=#111111][FONT=Arial, sans-serif]Sync pockets[/FONT][/COLOR][/h][LEFT][COLOR=#111111][FONT=Arial, sans-serif]**We can sync only one pocket at a time. Once one pocket sync is done, we can start the next one. This command will start the actual mirroring process for the **[/FONT][/COLOR][COLOR=#111111][FONT=Arial, sans-serif]**release**[/FONT][/COLOR][COLOR=#111111][FONT=Arial, sans-serif]** pocket:**[/FONT][/COLOR]

[/LEFT][COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif][FONT=Arial, sans-serif]landscape-api sync-mirror-pocket release [/FONT][/FONT][/COLOR][COLOR=#242729][COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]bionic[/FONT][/COLOR][COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif] ubuntu[/FONT][/COLOR][/COLOR]
[COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif][FONT=Arial, sans-serif]landscape-api sync-mirror-pocket updates bionic ubuntu[/FONT][/FONT][/COLOR]
[COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif][FONT=Arial, sans-serif]landscape-api sync-mirror-pocket [/FONT][/FONT][/COLOR][COLOR=#242729][COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]security[/FONT][/COLOR][COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif] [/FONT][/COLOR][COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]bionic [/FONT][/COLOR][COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]ubuntu[/FONT][/COLOR][/COLOR]

[LEFT][FONT=Arial, sans-serif]https://docs.ubuntu.com/landscape/en/repositories[/FONT][/LEFT]

---

### Post by james.w.krych on 2019-03-04
**Well... got the following error at 99%!** :mad:

Calculating packages to get...
Getting packages...
Got 1%: 1G 14M bytes
Got 2%: 1G 997M bytes
Got 3%: 3G 258M bytes
Got 4%: 3G 968M bytes
Got 5%: 5G 419M bytes
Got 6%: 5G 935M bytes
Got 7%: 6G 919M bytes
Got 8%: 8G 161M bytes
Got 9%: 8G 885M bytes
Got 10%: 9G 870M bytes
Got 11%: 10G 899M bytes
Got 12%: 11G 859M bytes
Got 13%: 12G 827M bytes
Got 14%: 13G 874M bytes
Got 15%: 14G 871M bytes
Got 16%: 15G 844M bytes
Got 17%: 16G 824M bytes
Got 18%: 17G 750M bytes
Got 19%: 18G 737M bytes
Got 20%: 19G 716M bytes
Got 21%: 20G 702M bytes
Got 22%: 21G 689M bytes
Got 23%: 22G 675M bytes
Got 24%: 23G 676M bytes
Got 25%: 24G 641M bytes
Got 26%: 25G 631M bytes
Got 27%: 26G 610M bytes
Got 28%: 27G 600M bytes
Got 29%: 28G 578M bytes
Got 30%: 29G 596M bytes
Got 31%: 30G 547M bytes
Got 32%: 31G 532M bytes
Got 33%: 32G 516M bytes
Got 34%: 33G 500M bytes
Got 35%: 34G 486M bytes
Got 36%: 35G 471M bytes
Got 37%: 36G 457M bytes
Got 38%: 37G 448M bytes
Got 39%: 38G 425M bytes
Got 40%: 39G 410M bytes
Got 41%: 40G 393M bytes
Got 42%: 41G 377M bytes
Got 43%: 42G 363M bytes
Got 44%: 43G 403M bytes
Got 45%: 44G 348M bytes
Got 46%: 45G 695M bytes
Got 47%: 46G 329M bytes
Got 48%: 47G 288M bytes
aptmethod error receiving '[http://archive.ubuntu.com/ubuntu/pool/universe/o/onedrive/onedrive_1.1.20170919-2ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/onedrive/onedrive_1.1.20170919-2ubuntu2_i386.deb)':
'401  Access Denied [IP: 91.189.88.149 80]'
Got 49%: 48G 299M bytes
Got 50%: 49G 261M bytes
Got 51%: 50G 246M bytes
Got 52%: 51G 229M bytes
Got 53%: 52G 208M bytes
Got 54%: 53G 455M bytes
Got 55%: 54G 180M bytes
Got 56%: 55G 767M bytes
Got 57%: 56G 148M bytes
Got 58%: 57G 140M bytes
Got 59%: 58G 603M bytes
Got 60%: 59G 116M bytes
Got 61%: 60G 106M bytes
Got 62%: 61G 129M bytes
Got 63%: 62G 159M bytes
Got 64%: 63G 326M bytes
Got 65%: 64G 206M bytes
Got 66%: 65G 29M bytes
Got 67%: 65G 1017M bytes
Got 68%: 67G 22M bytes
Got 69%: 67G 1013M bytes
Got 70%: 68G 980M bytes
Got 71%: 69G 982M bytes
Got 72%: 70G 941M bytes
Got 73%: 71G 928M bytes
Got 74%: 72G 912M bytes
Got 75%: 73G 899M bytes
Got 76%: 74G 885M bytes
Got 77%: 75G 875M bytes
Got 78%: 76G 849M bytes
Got 79%: 78G 37M bytes
Got 80%: 78G 848M bytes
Got 81%: 79G 805M bytes
Got 82%: 80G 786M bytes
Got 83%: 81G 770M bytes
Got 84%: 82G 782M bytes
Got 85%: 83G 740M bytes
Got 86%: 84G 725M bytes
aptmethod error receiving '[http://archive.ubuntu.com/ubuntu/pool/universe/o/onedrive/onedrive_1.1.20170919-2ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/onedrive/onedrive_1.1.20170919-2ubuntu2_amd64.deb)':
'401  Access Denied [IP: 91.189.88.162 80]'
Got 87%: 85G 779M bytes
Got 88%: 86G 694M bytes
Got 89%: 87G 692M bytes
Got 90%: 88G 694M bytes
Got 91%: 89G 649M bytes
Got 92%: 90G 823M bytes
Got 93%: 91G 616M bytes
Got 94%: 92G 609M bytes
Got 95%: 93G 660M bytes
Got 96%: 94G 598M bytes
Got 97%: 95G 556M bytes
Got 98%: 96G 540M bytes
Got 99%: 97G 524M bytes
90544 files were added but not used.
The next deleteunreferenced call will delete them.
There have been errors!

**Then, when I tried right again..**.


Sync pocket 'release' of series 'bionic' in distribution 'ubuntu'

Calculating packages to get...
Getting packages...
aptmethod error receiving '[http://archive.ubuntu.com/ubuntu/pool/universe/o/onedrive/onedrive_1.1.20170919-2ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/onedrive/onedrive_1.1.20170919-2ubuntu2_i386.deb)':
'401  Access Denied [IP: 91.189.88.161 80]'
aptmethod error receiving '[http://archive.ubuntu.com/ubuntu/pool/universe/o/onedrive/onedrive_1.1.20170919-2ubuntu2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/o/onedrive/onedrive_1.1.20170919-2ubuntu2_amd64.deb)':
'401  Access Denied [IP: 91.189.88.161 80]'
There have been errors!

[B]

I really, really don't want to start over again.

Best,
James


[/B]

---

### Post by james.w.krych on 2019-03-05
Had to anyway. This time, I eliminated the i386 architecture.

We'll see how this goes.

---

### Post by james.w.krych on 2019-03-07
Nope. :mad:

Failed AGAIN at 99%.

Is there not any singular Landscape support forum?

---

### Post by james.w.krych on 2019-03-08
I tried using the us.archive.ubuntu.com site, and though much faster, I got the same results:

Calculating packages to get...
Getting packages...
Got 1%: 784M 408K bytes
Got 2%: 1G 484M bytes
Got 3%: 2G 176M bytes
Got 4%: 2G 961M bytes
Got 5%: 4G 58M bytes
Got 6%: 4G 372M bytes
Got 7%: 5G 110M bytes
Got 8%: 5G 806M bytes
Got 9%: 6G 522M bytes
Got 10%: 7G 239M bytes
Got 11%: 7G 980M bytes
Got 12%: 8G 697M bytes
Got 13%: 9G 426M bytes
Got 14%: 10G 133M bytes
Got 15%: 10G 875M bytes
Got 16%: 11G 653M bytes
Got 17%: 12G 306M bytes
Got 18%: 13G 30M bytes
Got 19%: 13G 809M bytes
Got 20%: 14G 510M bytes
Got 21%: 15G 205M bytes
Got 22%: 16G 503M bytes
Got 23%: 16G 652M bytes
Got 24%: 17G 369M bytes
Got 25%: 18G 88M bytes
Got 26%: 18G 845M bytes
Got 27%: 19G 588M bytes
Got 28%: 20G 368M bytes
Got 29%: 20G 1010M bytes
Got 30%: 21G 746M bytes
Got 31%: 22G 447M bytes
Got 32%: 23G 160M bytes
Got 33%: 23G 932M bytes
Got 34%: 24G 616M bytes
Got 35%: 25G 338M bytes
Got 36%: 26G 44M bytes
Got 37%: 26G 808M bytes
Got 38%: 27G 832M bytes
Got 39%: 28G 283M bytes
Got 40%: 28G 955M bytes
Got 41%: 29G 779M bytes
Got 42%: 30G 415M bytes
Got 43%: 31G 106M bytes
Got 44%: 31G 846M bytes
Got 45%: 32G 630M bytes
Got 46%: 33G 294M bytes
Got 47%: 34G 11M bytes
Got 48%: 34G 737M bytes
Got 49%: 35G 454M bytes
Got 50%: 36G 175M bytes
Got 51%: 36G 910M bytes
Got 52%: 37G 627M bytes
Got 53%: 38G 491M bytes
Got 54%: 39G 68M bytes
Got 55%: 39G 804M bytes
Got 56%: 40G 519M bytes
Got 57%: 41G 235M bytes
Got 58%: 41G 976M bytes
Got 59%: 42G 700M bytes
Got 60%: 43G 409M bytes
Got 61%: 44G 174M bytes
Got 62%: 44G 872M bytes
Got 63%: 45G 584M bytes
Got 64%: 46G 314M bytes
Got 65%: 47G 156M bytes
aptmethod error receiving 'http://us.archive.ubuntu.com/ubuntu/pool/universe/o/onedrive/onedrive_1.1.20170919-2ubuntu2_amd64.deb':
'401  Access Denied [IP: 91.189.91.23 80]'
Got 66%: 47G 767M bytes
Got 67%: 48G 479M bytes
Got 68%: 49G 190M bytes
Got 69%: 49G 931M bytes
Got 70%: 50G 651M bytes
Got 71%: 51G 389M bytes
Got 72%: 52G 87M bytes
Got 73%: 52G 823M bytes
Got 74%: 53G 606M bytes
Got 75%: 54G 261M bytes
Got 76%: 55G 696M bytes
Got 77%: 55G 721M bytes
Got 78%: 56G 431M bytes
Got 79%: 57G 147M bytes
Got 80%: 57G 887M bytes
Got 81%: 58G 612M bytes
Got 82%: 59G 321M bytes
Got 83%: 60G 47M bytes
Got 84%: 60G 955M bytes
Got 85%: 61G 799M bytes
Got 86%: 62G 339M bytes
Got 87%: 62G 957M bytes
Got 88%: 63G 802M bytes
Got 89%: 64G 488M bytes
Got 90%: 65G 119M bytes
Got 91%: 65G 847M bytes
Got 92%: 66G 577M bytes
Got 93%: 67G 287M bytes
Got 94%: 67G 1016M bytes
Got 95%: 68G 733M bytes
Got 96%: 69G 449M bytes
Got 97%: 70G 173M bytes
Got 98%: 70G 975M bytes
Got 99%: 71G 643M bytes
60865 files were added but not used.
The next deleteunreferenced call will delete them.
There have been errors!


Why is this error

[B]aptmethod error receiving 'http://us.archive.ubuntu.com/ubuntu/pool/universe/o/onedrive/onedrive_1.1.20170919-2ubuntu2_amd64.deb':
'401  Access Denied [IP: 91.189.91.23 80]'[/B]

Happening? Also, how can the sync get to 99% and still fail?

Anybody out here experienced this issue with Landscape?

---

### Post by james.w.krych on 2019-03-08
These two worked and were successfully completed:
[COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif][FONT=Arial, sans-serif]landscape-api sync-mirror-pocket updates bionic ubuntu[/FONT][/FONT][/COLOR]
[COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif][FONT=Arial, sans-serif]landscape-api sync-mirror-pocket [/FONT][/FONT][/COLOR][COLOR=#242729][COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]security[/FONT][/COLOR][COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif] [/FONT][/COLOR][COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]bionic [/FONT][/COLOR][COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]ubuntu

But, I am still having a failure with this:
[/FONT][/COLOR][/COLOR]
[COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif][FONT=Arial, sans-serif]landscape-api sync-mirror-pocket release [/FONT][/FONT][/COLOR][COLOR=#242729][COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]bionic[/FONT][/COLOR][COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif] ubuntu

Getting the following error:
[/FONT][/COLOR][/COLOR][h=3]Details[/h][TABLE]
[TR="class: completed-detail"]
[TD="class: tight-fit"]Completed at:[/TD]
[TD="class: time-detail"]Today at 12:47 EST[/TD]
[/TR]
[/TABLE]

Calculating packages to get...
Getting packages...
aptmethod error receiving 'http://us.archive.ubuntu.com/ubuntu/pool/universe/o/onedrive/onedrive_1.1.20170919-2ubuntu2_amd64.deb':
'401  Access Denied [IP: 91.189.91.26 80]'
There have been errors!

---

### Post by james.w.krych on 2019-03-12
[COLOR=#242729][FONT=Arial]As of this time, 12 MAR 2-19, it seems the issue is on our end but we are at a loss as to why.[/FONT][/COLOR][COLOR=#242729][FONT=Arial] [/FONT][/COLOR]

---

### Post by james.w.krych on 2019-03-15
Seems to have been resolved behind the scenes.

---

