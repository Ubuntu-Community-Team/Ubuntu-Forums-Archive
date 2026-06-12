---
title: "Need help uploading newer version to launchpad launchpad."
date: 2016-06-20
forum: Ubuntu Application Development
---

### Post by CantankRus on 2016-06-20
I'm having trouble understanding how to upload a newer version to my ppa.
I've only just created a ppa and successfully uploaded my first deb.
I've made some changes in a couple of scripts in the package and want to update the ppa.

I understand you have to make a change to the debian/changelog to reflect the new version.
I did this (not even sure if thats the correct way to number)...
```
quicksnips (0.2-1) xenial; urgency=low

  * Now adds the sample snippets.txt to users home.
  * Added check for presence of quicksnips.desktop on launcher.
  * Insert Date changed to output date and time in RFC 2822 format.

 -- Glen Shrubsall <xxx@westnet.com.au>  Mon, 20 Jun 2016 16:36:41 +0800

quicksnips (0.1-1) xenial; urgency=medium

  * Initial release.

 -- Glen Shrubsall <xxx@westnet.com.au>  Sun, 19 Jun 2016 20:02:19 +0800 
```

What's the actual process and what files do I need when uploading a newer version?
Do I need all the original files or just archives?
This is the [**PPA**]("https://launchpad.net/~stinkeye/+archive/ubuntu/quicksnips").

---

### Post by CantankRus on 2016-06-20
What did we do before google?
Found the answer [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://askubuntu.com/questions/164621/how-do-i-add-a-binary-file-to-my-existing-ppa-package") 
As part of the process use ...
```
dpkg-source --commit
```
to create a patch.

---

### Post by QDR06VV9 on 2016-06-20
Great Detective work CantankRus!:)
Thanks for the share also.
Best Regards

---

### Post by CantankRus on 2016-06-20
> **runrickus said:**
> Great Detective work CantankRus!:)
Thanks for the share also.
Best Regards
Thanks,
You can call me Sam Spade. :P
This PPA stuff is hard slog.

---

### Post by mc4man on 2016-06-20
> **CantankRus said:**
> What did we do before google?
Found the answer [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://pifuge.com/ubuntu/IRu-how-do-i-add-a-binary-file-to-my-existing-ppa-package") 
As part of the process use ...
```
dpkg-source --commit
```
to create a patch.
If you're using a source format (debian/source/format) of 3.0 (quilt)  then any changes to the source must be committed first & provided via a patch. (as you've seen
This is mainly because & to leave  the orig source  unchanged. 
However in your changelog you have also altered the source version so it's likely you'll need to create  & upload a new .orig to reflect that.
In this case you didn't need to do that, the new upload changelog version could have been something like - 

quicksnips (0.1-[COLOR="#0000CD"]1.1[/COLOR]) xenial; urgency=low
or
quicksnips (0.1-[COLOR="#0000CD"]2[/COLOR]) xenial; urgency=low
or
 start the first/original upload  with a ~ in package version, ie. - 
quicksnips (0.1-1~ppa) xenial; urgency=low
Then if you happen to need to adjust something 
quicksnips (0.1-1~ppa1) xenial; urgency=low
quicksnips (0.1-1~ppa2) xenial; urgency=low
ect.
In all of the above cases you can reuse the original source & uploads would just be of the changes

---

### Post by CantankRus on 2016-06-20
Thank you mc3+1man.

---

### Post by mc4man on 2016-06-20
I see you got around by adding ubuntu1 to the package name but keeping orig. source version (0.1)
That also works, myself try not to use ubuntu in name unless ubuntu already altered a source & I'm futher changing, then I'd usually go whaterever.1~ppaX
ex. my personal unity package is - blue my addition

unity (7.5.0+16.10.20160517-0ubuntu1[COLOR="#0000CD"].1~ppa[/COLOR]) xenial;

The .1 makes it higher than ubuntu's package, the ~ppa  signifies my changes & keeps the package below a possible repo update. (not likely with unity as it's always date based but theory is the same.
eg.
7.5.0+16.10.20160517-0ubuntu1 # current ubuntu
7.5.0+16.10.20160517-0ubuntu1.1~ppa # is a higher version
7.5.0+16.10.20160517-0ubuntu1.1 # is a higher version than mine, the tilde causes that

---

### Post by CantankRus on 2016-06-20
More by accident than choice.
The "**dhc -i**" command added the numbering template to my original changelog...
```
 [B]quicksnips (0.1-1ubuntu1) UNRELEASED; urgency=medium

  * 

 -- Glen Shrubsall <xxx@westnet.com.au>  Tue, 21 Jun 2016 01:14:44 +0800[/B]

quicksnips (0.1-1) xenial; urgency=medium

  * Initial release.

 -- Glen Shrubsall <xxx@westnet.com.au>  Sun, 19 Jun 2016 20:02:19 +0800 
```
Thanks, the more info the better.

---

