---
title: "How to change permission to a File/Folder in US from the GUI?"
date: 2017-02-06
forum: Ubuntu Studio
---

### Post by bottye2 on 2017-02-06
Hi all, I'm new for Ubuntu and Studio (in general about linux).

How can I change permission to a file/folder from the xfce interface files browser?

Thank you!

E-

---

### Post by ajgreeny on 2017-02-06
You can right click on the file, choose **Properties**, and then go to the **Permissions** tab.

What file or files do you need to edit as you can only change the permissions of your own files in your home folder; any files in the OS itself will need temporary elevation to root to do the same action as they are owned by root.
If you feel you must do that using the file-manager, which I think is thunar in U-Studio, you will need to start the file-manager as root either using ```
gksudo thunar
``` or ```
sudo -H thunar
``` but be very careful using the file manager as root as you could do great damage to the whole system if you are not careful.

**DO NOT USE** **sudo thunar **or you could cause user login problems for yourself.

---

### Post by bottye2 on 2017-02-09
WOW, great!

Thanks a lot!!!
I try to ask here other 4 little question, I don't know if I can in this area. :)
[LIST=1]
[*]I tried to install Celtx and it seems that is near ok ( after many attempts that I must to remove :-( ) but it seems that it can't find the libpng12 library, how can I install it?

I tried this but goes bad:

> sudo apt-get install libpng12-0
[sudo] password di bottye: 
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Il pacchetto libpng12-0 non ha versioni disponibili, ma è nominato da un altro
pacchetto. Questo potrebbe indicare che il pacchetto è mancante, obsoleto
oppure è disponibile solo all'interno di un'altra sorgente

E: Il pacchetto "libpng12-0" non ha candidati da installare



The pack has no candidates to be install...
:(
[*]How can I remove the descriptions near the open folders/programs icons in Panel?
[*]How can I reopen folders/programs automatically when US restart?
[*]How can I reopen folders/tabs automatically when Thunar restart?
[/LIST]

Many many thanks in advance!!!

E-

---

