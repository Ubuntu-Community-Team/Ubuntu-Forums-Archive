---
title: "xenial, can't update fonts unmet dependencies"
date: 2016-01-13
forum: Ubuntu Development Version
---

### Post by pixelro on 2016-01-13
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 fonts-tlwg-garuda : Depends: fonts-tlwg-garuda-ttf but it is not installed or
                              fonts-tlwg-garuda-otf but it is not installed
 fonts-tlwg-kinnari : Depends: fonts-tlwg-kinnari-ttf but it is not installed or
                               fonts-tlwg-kinnari-otf but it is not installed
 fonts-tlwg-laksaman : Depends: fonts-tlwg-laksaman-ttf but it is not installed or
                                fonts-tlwg-laksaman-otf but it is not installed
 fonts-tlwg-loma : Depends: fonts-tlwg-loma-ttf but it is not installed or
                            fonts-tlwg-loma-otf but it is not installed
 fonts-tlwg-mono : Depends: fonts-tlwg-mono-ttf but it is not installed or
                            fonts-tlwg-mono-otf but it is not installed
 fonts-tlwg-norasi : Depends: fonts-tlwg-norasi-ttf but it is not installed or
                              fonts-tlwg-norasi-otf but it is not installed
 fonts-tlwg-purisa : Depends: fonts-tlwg-purisa-ttf but it is not installed or
                              fonts-tlwg-purisa-otf but it is not installed
 fonts-tlwg-sawasdee : Depends: fonts-tlwg-sawasdee-ttf but it is not installed or
                                fonts-tlwg-sawasdee-otf but it is not installed
 fonts-tlwg-typewriter : Depends: fonts-tlwg-typewriter-ttf but it is not installed or
                                  fonts-tlwg-typewriter-otf but it is not installed
 fonts-tlwg-typist : Depends: fonts-tlwg-typist-ttf but it is not installed or
                              fonts-tlwg-typist-otf but it is not installed
 fonts-tlwg-typo : Depends: fonts-tlwg-typo-ttf but it is not installed or
                            fonts-tlwg-typo-otf but it is not installed
 fonts-tlwg-umpush : Depends: fonts-tlwg-umpush-ttf but it is not installed or
                              fonts-tlwg-umpush-otf but it is not installed
 fonts-tlwg-waree : Depends: fonts-tlwg-waree-ttf but it is not installed or
                             fonts-tlwg-waree-otf but it is not installed
E: Unmet dependencies. Try using -f.


bug report here [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1533543](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1533543)

---

### Post by zika on 2016-01-13
```
sudo [COLOR=#000000]apt-get install[/COLOR][COLOR=#000000] -f[/COLOR]
```[COLOR=#000000]as You were advised...?[/COLOR]

---

### Post by pixelro on 2016-01-13
> **zika said:**
> ```
sudo [COLOR=#000000]apt-get install[/COLOR][COLOR=#000000] -f[/COLOR]
```[COLOR=#000000]as You were advised...?[/COLOR]
thanks, solved :D i feel stupid now :))

---

### Post by zika on 2016-01-13
> **pixelro said:**
> thanks, solved :D i feel stupid now :))Please do not feel that way. If somene would have gave me a $ every time I felt like that I would be... You get it... ;) That is why we are all here. I just do have greater mileage in feeling like that so I could dig out a solution faster... :-\"

---

