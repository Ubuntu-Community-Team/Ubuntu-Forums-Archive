---
title: "firefox 3.6 and thunderbird 3 without 'daily'"
date: 2010-01-23
forum: Ubuntuzilla
---

### Post by BartVanGils on 2010-01-23
I'm now using Firefox 3.5.7 and Thunderbird 2.0.0.23.

Is it possible to upgrade firefox and thunderbird to their latest stable versions: Firefox 3.6 and Thunderbird 3 using the repositories?
If yes, how can I do this?

---

### Post by ajgreeny on 2010-01-23
Google **thunderbird ppa** and you will find lots of info.  Same for firefox.

---

### Post by nanotube on 2010-01-23
> **BartVanGils said:**
> I'm now using Firefox 3.5.7 and Thunderbird 2.0.0.23.

Is it possible to upgrade firefox and thunderbird to their latest stable versions: Firefox 3.6 and Thunderbird 3 using the repositories?
If yes, how can I do this?

the ubuntuzilla ppa will let you upgrade both firefox and thunderbird to the latest stable mozilla releases. 

if you're looking for the stable releases, do NOT use the ubuntu-mozilla-daily ppa, since those are nightly builds, not releases.

see [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
for instructions.

---

### Post by BartVanGils on 2010-01-25
> **nanotube said:**
> the ubuntuzilla ppa will let you upgrade both firefox and thunderbird to the latest stable mozilla releases. 

if you're looking for the stable releases, do NOT use the ubuntu-mozilla-daily ppa, since those are nightly builds, not releases.

see [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
for instructions.

Thank you very much. This works perfect!

Just as extra information: after installation:
- Firefox 3.6 uses the same profile as the previous version
- for Thunderbird 3.0, I had to transfer the profile-map of my 'old' Thunderbird to the 'new' Thunderbird.

---

### Post by maedox on 2010-01-25
Here is what I did:
Download the latest release of Firefox from Mozilla's website. Extract it anywhere you want and make a link to the executable 'firefox' in '/usr/local/bin/'.

If you extracted the files to /opt/firefox/ do the following in terminal:
```
ln -s /opt/firefox/firefox /usr/local/bin/firefox
```

You can leave the one from the Ubuntu repository installed, because the link in /usr/local/bin will be the primary.

---

### Post by Haber_Nir on 2010-01-25
is there thunderbird ppa (stable) for ubuntu 64bit?
becuase ubuntuzilla is for 32bit only

---

### Post by nanotube on 2010-01-25
> **Haber_Nir said:**
> is there thunderbird ppa (stable) for ubuntu 64bit?
becuase ubuntuzilla is for 32bit only

unfortunately no - not that i'm aware of.

---

### Post by wondermac on 2010-01-26
I installed the source according to the ubuntuzilla website. however, when I try to update the respositories, the following error occurs:

> Err [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release.gpg                           
  Could not connect to nchc.dl.sourceforge.net:80 (211.79.60.17), connection timed out
Reading package lists... Done                             
W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release.gpg](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release.gpg)  Could not connect to nchc.dl.sourceforge.net:80 (211.79.60.17), connection timed out

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problemswhat can I do?

thanks for your help!

---

### Post by nanotube on 2010-01-27
> **wondermac said:**
> I installed the source according to the ubuntuzilla website. however, when I try to update the respositories, the following error occurs:

what can I do?

thanks for your help!

seems that the mirror you were directed to is/was having difficulties... just give it another try.

---

### Post by wondermac on 2010-01-27
> seems that the mirror you were directed to is/was having difficulties... just give it another try.

doesn't seem to work. can I actively influence the mirror chosen?

---

### Post by nanotube on 2010-01-27
> **wondermac said:**
> doesn't seem to work. can I actively influence the mirror chosen?

well, only by specifying it directly...

try editing your sources.list, and instead of 'downloads.sourceforge.net' use "switch.dl.sourceforge.net" (leaving everything else the same).

switch.dl is one of the sf mirrors that's usually pretty good... give that a try and let me know how it goes...

---

### Post by wondermac on 2010-01-27
> **nanotube said:**
> 
try editing your sources.list, and instead of 'downloads.sourceforge.net' use "switch.dl.sourceforge.net" (leaving everything else the same).


I get this:

> W: Failed to fetch [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by aysiu on 2010-01-27
There's no 64-bit official stable Firefox 3.6. You'll have to use the daily build PPA.

---

### Post by nanotube on 2010-01-27
ah, well, now we run into another problem: it seems that you haven't noticed the prominent info box on the ubuntuzilla website that says "this repository only contains 32bit packages". 

unfortunately you have to look for another source.

if you go to [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) and click to the section on 64bit users, it lists some possible alternatives for 64bit users. 

if you're only looking for firefox, your best bet is the firefox-stable ppa.

---

### Post by wondermac on 2010-01-27
> **aysiu said:**
> There's no 64-bit official stable Firefox 3.6. You'll have to use the daily build PPA.

I thought of just using the 32bit versions with the necessary libraries (as I do now with Firefox 3.5.7 and Thunderbird 2.0.0.23). 

How can I do this? (sorry, I'm quite new to Ubuntu)

---

### Post by nanotube on 2010-01-27
> **aysiu said:**
> There's no 64-bit official stable Firefox 3.6. You'll have to use the daily build PPA.

aysiu, fyi:

it seems they just rolled out a firefox-stable ppa on launchpad a day or two ago.

only for firefox, though... but i'd recommend it above the daily, for 64bit users that are looking for firefox.

[https://launchpad.net/~mozillateam/+archive/firefox-stable/](https://launchpad.net/~mozillateam/+archive/firefox-stable/)

---

### Post by aysiu on 2010-01-27
> **nanotube said:**
> aysiu, fyi:

it seems they just rolled out a firefox-stable ppa on launchpad a day or two ago.

only for firefox, though... but i'd recommend it above the daily, for 64bit users that are looking for firefox.

[https://launchpad.net/~mozillateam/+archive/firefox-stable/](https://launchpad.net/~mozillateam/+archive/firefox-stable/)
Cool. Good to know.

---

### Post by nanotube on 2010-01-27
> **wondermac said:**
> I thought of just using the 32bit versions with the necessary libraries (as I do now with Firefox 3.5.7 and Thunderbird 2.0.0.23. How can I do this? (sorry, I'm quite new to Ubuntu)

before you go down that road, i'd suggest trying the firefox-stable ppa.

for thunderbird... either try the daily ppa, or the old ubuntuzilla installer script. (all this is described on the ubuntuzilla website in the 64bit user section).

alternatively, you could technically grab the .debs directly from the downloads section, and install them with "dpkg -i --force-architecture", and make sure to manually install the 32bit compat libraries. but i'd probably leave that for a last resort. :)

---

### Post by wondermac on 2010-01-27
> **nanotube said:**
> before you go down that road, i'd suggest trying the firefox-stable ppa.

for thunderbird... either try the daily ppa, or the old ubuntuzilla installer script. (all this is described on the ubuntuzilla website in the 64bit user section).



I successfully installed firefox from the 'new' source. now if I consider to go for daily build of thunderbird, (how) can I ensure, that only thunderbird gets the daily updates, but not firefox?

Thanks guys for your help, I very much appreciate that!

---

### Post by nanotube on 2010-01-27
> **wondermac said:**
> I successfully installed firefox from the 'new' source. now if I consider to go for daily build of thunderbird, (how) can I ensure, that only thunderbird gets the daily updates, but not firefox?

Thanks guys for your help, I very much appreciate that!

hrm, actually... i do not know. 

you could maybe 'pin' the firefox to the version at 3.6, but then that means if 3.6.1 is released in firefox-stable, it won't prompt you for update... 

or you could install thunderbird, then disable the daily ppa - but that would leave you without further thunderbird updates. 

maybe someone can think of a better solution...

or you could just avoid the daily repo, and try installing tb3 32bit from mozilla, either manually or using the old ubuntuzilla script...

---

### Post by BartVanGils on 2010-02-06
Since I installed Firefox 3.6 (stable release, using Ubuntuzilla), I have now the problem, when I close Firefox, that there 2 processes are still active:
- firefox (doing nothing)
- firefox.bin (taking a lot of CPU time)

When I want to restart Firefox, I get a message that Firefox is still running...

Are there other users with the same problem?
How can I fix this?

---

### Post by nanotube on 2010-02-06
> **BartVanGils said:**
> Since I installed Firefox 3.6 (stable release, using Ubuntuzilla), I have now the problem, when I close Firefox, that there 2 processes are still active:
- firefox (doing nothing)
- firefox.bin (taking a lot of CPU time)

When I want to restart Firefox, I get a message that Firefox is still running...

Are there other users with the same problem?
How can I fix this?

does the problem persist if you start with a fresh profile?

---

### Post by BartVanGils on 2010-02-09
> **nanotube said:**
> does the problem persist if you start with a fresh profile?

With a fresh profile, the problem doesn't persist.

---

### Post by nanotube on 2010-02-09
> **BartVanGils said:**
> With a fresh profile, the problem doesn't persist.

well, then it must be either one of the addons you have or something else in your profile that's confusing firefox. 

either uninstall some addons from the old profile until it goes away, or just use the fresh profile, import your old bookmarks, install afresh the addons that you want. (i recommend the latter).

---

### Post by tmetro on 2010-06-09
> **nanotube said:**
> 
you could maybe 'pin' the firefox to the version at 3.6, but then that means if 3.6.1 is released in firefox-stable, it won't prompt you for update... 

or you could install thunderbird, then disable the daily ppa - but that would leave you without further thunderbird updates. 

maybe someone can think of a better solution...

I used the stable PPA for FF 3.6, and then installed the daily PPA for TB, and added the following to /etc/apt/preferences:

```

# install TB 3.0 from ubuntu-mozilla-daily PPA
Package: thunderbird-3.0
Pin: release o=LP-PPA-ubuntu-mozilla-daily
Pin-Priority: 500

# don't install ubuntu-mozilla-daily packages by default
Package: *
Pin: release o=LP-PPA-ubuntu-mozilla-daily
Pin-Priority: 400

```

(I found the origin name of the PPA by examining the [Release]("http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/dists/karmic/main/binary-amd64/Release") file.)

Before pinning I get:

```

% apt-cache policy firefox-3.6
firefox-3.6:
  Installed: 3.6+karmic
  Candidate: 3.6+karmic
  Version table:
 *** 3.6+karmic 0
        500 http://ppa.launchpad.net karmic/main Packages
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status

```

And after:

```

% apt-cache policy firefox-3.6
firefox-3.6:
  Installed: 3.6+karmic
  Candidate: 3.6+karmic
  Version table:
 *** 3.6+karmic 0
        500 http://ppa.launchpad.net karmic/main Packages
        400 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status

```

Unfortunately all the PPAs look alike in this report, but note the second one has dropped to a 400 priority, which is the daily PPA, and will avoid using that PPA for all but the specified TB package.

 -Tom

---

