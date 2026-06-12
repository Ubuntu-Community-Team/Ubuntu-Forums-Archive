---
title: "Eye of GNOME 2.14 (eog-2.14)"
date: 2006-03-14
forum: Ubuntu Backports
---

### Post by magnusbb on 2006-03-14
Following a backport of Deskbar-applet (which is version 0.8.5 in the official backports), I have now brought Eye of GNOME up to the latest 2.14 release over the 2.13.2 package provided in the offiicial backports.

It may be wise to uninstall your original version of eog and delete its gconf-keys and config files prior to installing this.

According to the developers the following is new to this version from 2.13.2:

```
Version 2.14.0
---------------
- Fixes crasher when opening images with strange extensions 
  (Ryan Lortie) [#333551]
- Quit EOG when not able to load images (Lucas Rocha)
- Fix window positioning behavior (Lucas Rocha) 
- Updated translations: Alexander Shopov (bg), Mugurel Tudor (ro),
  Rajesh Ranjan (hi), Luca Ferretti (it), Ole Laursen (da),
  Gabor Kelemen (hu), Daniel Nylander (sv), Elnaz Sarbar (fa),
  Farzaneh Sarafraz (fa), Miloslav Trmac (cs), Benoît Dejean (fr). 

Version 2.13.92
---------------

- Disable all debug messages by default (Lucas Rocha) [#331362]
- Fix 64-bit pointer truncation (Pascal Hofstee, Alexander 
  Nedotsukov) [#331971] 
- Correct handling of zoom precision with mouse wheel 
  (Felix Riemann) [#310833] 
- Build system fixes (Sylvain Bertrand) [#330708]
- Define a minimum window size (Lucas Rocha) [#327065]
- Mouse scroll wheel now makes image switching on collection 
  pane (Lucas Rocha) [#331645]
- Fixes crash when removing images from a directory with images 
  that EOG is watching (Lucas Rocha)
- Updated translations: Žygimantas Beru&#269;ka (lt), Kostas Papadimas (el),
  Satoru Satoh (ja), Inaki Larrañaga (eu), Artur Flinta (pl),
  Rhys Jones (cy), Leonid Kanter (ru), Alessio Frusciante (it),
  Maxim Dziumanenko (uk)

Version 2.13.91
---------------

- Remove critical warnings on save dialogs (Lucas Rocha) [#327170]
- Use current locale for images on NIS filesystem (Takao Fujiwara) [320289] 
- Updated translations: Laurent Dhima (sq), Hendrik Richter (de),
  Lukas Novotny (cs), Alexander Sigachov (ru)  

Version 2.13.90
---------------

- Normal viewing of images from SMB shares (#326104)
  Patch from Felix Riemann.
- .desktop file fixes (#328033)
- Updated translations:  Theppitak Karoonboonyanan (th), Ankit Patel (gu),
  Adam Weinberger (en_CA), Slobodan D. Sredojevic (sr, sr@Latn), 
  Priit Laes (et), Clytie Siddall (vi), Kjartan Maraas (no, nb),
  Josep Puigdemont i Casamajó (ca), Francisco Javier F. Serrador (es),
  Chao-Hsiung Liao (zh_TW, zh_HK), Funda Wang (zh_CN), Duarte Loreto (pt),
  Evandro Fernandez Giovanini (pt_BR)  

Version 2.13.5
--------------

- Plural string fixes (#327106)
- Updated translations: Clytie Siddall (vi), Ankit Patel (gu),
  Gabor Kelemen (hu), Ivar Smolin (et), Takeshi Aihana (ja),
  Kjartan Maraas (no, nb), Chao-Hsiung Liao (zh_TW, zh_HK),
  Francisco Javier F. Serrador (es), Slobodan D. Sredojevic (sr, sr@Latn),
  Ignacio Casal Quinteiro (gl), Ilkka Tuohela (fi)  


Version 2.13.4
--------------

- Disable xscreensaver on fullscreen mode (#326369)
- Correctly refresh image section for very small images (#317641).
  Patch from Felix Riemann.
- New delete confirmation dialog (#322884). Patch from
  Jaap Haitsma.
- Several code cleanups. Patches from Felix Riemann.
- Resize window according to the image dimensions (#323204)
- Add BackSpace accel for previous image action (#324088)
- Fix GTK+ dependency version. (#324149)
- Updated translations: Alan Horkan (en_GB), Clytie Siddall (vi),
  Ilkka Tuohela (fi), Abel Cheung (zh_TW, zh_HK), Josep Puigdemont 
  i Casamajó (ca), Žygimantas Beru&#269;ka (lt), Vincent van Adrighem (nl),
  Kjartan Maraas (no, nb), Ignacio Casal Quinteiro (gl), Theppitak
  Karoonboonyanan (th), Ankit Patel (gu), Alexander Shopov (bg),
  Adam Weinberger (en_CA) 

Version 2.13.3
--------------

- Added Return accelerator for Next Image and Shift+Return
  and Shift+SpaceBar accelerators for Previous Image. (#322593)
  Patch from Jaap A. Haitsma <jaap@haitsma.org>
- Use one single function when changing single selection
  instead of six too similar ones. (#321395) Patch from
  Claudio Saavedra <csaavedra@alumnos.utalca.cl>)
- Icon now shown in about dialog. (#321665) Patch from
  Vincent Noel <vincent.noel@gmail.com>.
- Image information pane is disabled by default. (#313672)
- Other assorted bug fixes and code cleanups.
- Updated translations: 
  Ankit Patel (gu), Alessio Frusciante (it), Miloslav Trmac (cs),
  Åsmund Skjæveland (nn),  Francisco Javier F. Serrador (es),
  Alexander Shopov (bg), Žygimantas Beru&#269;ka (lt),Ales Nyakhaychyk (be),
  Takeshi AIHANA (ja), Adam Weinberger (en_CA), Funda Wang (zh_CN),
  Priit Laes (et), Ignacio Casal Quinteiro (gl), Kjartan Maraas (nb, no),
  Guilherme de S. Pastore (pt_BR), Theppitak Karoonboonyanan (th).
```

---

### Post by elvislu on 2006-03-15
does it support gif animation now?

---

### Post by magnusbb on 2006-03-15
No, GIF animation, is not supported, it seems. You'll have to use gThumb for that.

---

