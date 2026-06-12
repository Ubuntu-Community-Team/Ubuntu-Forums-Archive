---
title: "Kernel compile and broken dependencies"
date: 2014-07-28
forum: Server Platforms
---

### Post by lorenzo9 on 2014-07-28
Hi all, 
I'm a newbie so please don't hurt me too much &#9786;
I'm dealing with a server in which I installed Ubuntu Server 14.04 LTS. In this server there is a Chelsio t4 10gb network adapter (t420-bt) which I want to use. 
After a long research I found that the only way to make this card working was to rebuild the kernel with proper configuration. 
So I followed this guide [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel) (apt-get way). 

The only thing that I changed in the configuration was to add chelsio t4 adapters. 
After the kernel building I got the following .deb packages:
```

-rw-r--r--  1 lorenzo lorenzo    135562 lug 27 18:18 linux-cloud-tools-3.13.0-32-generic_3.13.0-32.57_amd64.deb-rw-r--r--  1 lorenzo lorenzo   9022274 lug 27 15:40 linux-headers-3.13.0-32_3.13.0-32.57_all.deb
-rw-r--r--  1 lorenzo lorenzo    822784 lug 27 18:17 linux-headers-3.13.0-32-generic_3.13.0-32.57_amd64.deb
-rw-r--r--  1 lorenzo lorenzo  15330974 lug 27 18:16 linux-image-3.13.0-32-generic_3.13.0-32.57_amd64.deb
-rw-r--r--  1 lorenzo lorenzo  36886496 lug 27 18:17 linux-image-extra-3.13.0-32-generic_3.13.0-32.57_amd64.deb
-rw-r--r--  1 lorenzo lorenzo    135612 lug 27 18:17 linux-tools-3.13.0-32-generic_3.13.0-32.57_amd64.deb

```

Trying to install them all I got this:

```

lorenzo@mediaserver:~$ sudo dpkg -i linux*3.13.0-32.57*.deb
[sudo] password for lorenzo:
(Lettura del database... 168348 file e directory attualmente installati.)
Preparativi per estrarre linux-cloud-tools-3.13.0-32-generic_3.13.0-32.57_amd64.deb...
Estrazione di linux-cloud-tools-3.13.0-32-generic (3.13.0-32.57) su (3.13.0-32.57)...
Preparativi per estrarre linux-headers-3.13.0-32_3.13.0-32.57_all.deb...
Estrazione di linux-headers-3.13.0-32 (3.13.0-32.57) su (3.13.0-32.57)...
Preparativi per estrarre linux-headers-3.13.0-32-generic_3.13.0-32.57_amd64.deb...
Estrazione di linux-headers-3.13.0-32-generic (3.13.0-32.57) su (3.13.0-32.57)...
Preparativi per estrarre linux-image-3.13.0-32-generic_3.13.0-32.57_amd64.deb...
Done.
Estrazione di linux-image-3.13.0-32-generic (3.13.0-32.57) su (3.13.0-32.57)...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Preparativi per estrarre linux-image-extra-3.13.0-32-generic_3.13.0-32.57_amd64.deb...
Estrazione di linux-image-extra-3.13.0-32-generic (3.13.0-32.57) su (3.13.0-32.57)...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Preparativi per estrarre linux-tools-3.13.0-32-generic_3.13.0-32.57_amd64.deb...
Estrazione di linux-tools-3.13.0-32-generic (3.13.0-32.57) su (3.13.0-32.57)...
dpkg: problemi con le dipendenze impediscono la configurazione di linux-cloud-tools-3.13.0-32-generic:
 linux-cloud-tools-3.13.0-32-generic dipende da linux-cloud-tools-3.13.0-32; comunque:
  Il pacchetto linux-cloud-tools-3.13.0-32 non è installato.


dpkg: errore nell'elaborare il pacchetto linux-cloud-tools-3.13.0-32-generic (--install):
 problemi con le dipendenze - lasciato non configurato
Configurazione di linux-headers-3.13.0-32 (3.13.0-32.57)...
Configurazione di linux-headers-3.13.0-32-generic (3.13.0-32.57)...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Configurazione di linux-image-3.13.0-32-generic (3.13.0-32.57)...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled
(3.13.0-32.57 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(3.13.0-32.57 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Generating grub configuration file ...
Attenzione: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Trovata immagine linux: /boot/vmlinuz-3.13.0-32-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
fatto
Configurazione di linux-image-extra-3.13.0-32-generic (3.13.0-32.57)...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled
(3.13.0-32.57 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(3.13.0-32.57 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Generating grub configuration file ...
Attenzione: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Trovata immagine linux: /boot/vmlinuz-3.13.0-32-generic
Trovata immagine initrd: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
fatto
dpkg: problemi con le dipendenze impediscono la configurazione di linux-tools-3.13.0-32-generic:
 linux-tools-3.13.0-32-generic dipende da linux-tools-3.13.0-32; comunque:
  Il pacchetto linux-tools-3.13.0-32 non è installato.


dpkg: errore nell'elaborare il pacchetto linux-tools-3.13.0-32-generic (--install):
 problemi con le dipendenze - lasciato non configurato
Si sono verificati degli errori nell'elaborazione:
 linux-cloud-tools-3.13.0-32-generic
 linux-tools-3.13.0-32-generic

```

So I skipped linux-tools and linux-cloud-tools and the installation went good. 
The problem is that now if I try to use apt-get I get stacked with an error:

```

lorenzo@mediaserver:~$ sudo apt-get install iotop
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere questi problemi:
I seguenti pacchetti hanno dipendenze non soddisfatte:
 linux-cloud-tools-3.13.0-32-generic : Dipende: linux-cloud-tools-3.13.0-32 ma non sta per essere installato
 linux-tools-3.13.0-32-generic : Dipende: linux-tools-3.13.0-32 ma non sta per essere installato
E: Dipendenze non soddisfatte. Provare "apt-get -f install" senza pacchetti (o specificare una soluzione).

```

Can you help me with this? 

Ps: I'm sorry for the system language but I don't know how to change it. If you tell me how, I can try to re-past all the messages in English. 

Thanks a lot in advance 
Lorenzo

---

### Post by slooksterpsv on 2014-07-28
Well it wants that dependency so you can either remove what you just installed, install the missing dependency, or force the installation without it.

If you want to attempt to instal the missing dependency run: sudo apt-get install -f

---

### Post by lorenzo9 on 2014-07-28
Hi slooksterpsv, thanks for the reply. 

You mean: 
```

sudo apt-get install -f iotop

```
right?

Or do I have to try to install the missing dependencies? Because I also tried that 
```

sudo apt-get install linux-tools

```
and
```

sudo apt-get install linux-cloud-tools

```
but it didn't work

---

### Post by slooksterpsv on 2014-07-28
no just run:

sudo apt-get install -f

---

### Post by lorenzo9 on 2014-07-28
Hello all, 
I tried with 
```

lorenzo@mediaserver:~$ sudo apt-get -f install iotop
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere questi problemi:
I seguenti pacchetti hanno dipendenze non soddisfatte:
 linux-cloud-tools-3.13.0-32-generic : Dipende: linux-cloud-tools-3.13.0-32 ma non sta per essere installato
 linux-tools-3.13.0-32-generic : Dipende: linux-tools-3.13.0-32 ma non sta per essere installato
E: Dipendenze non soddisfatte. Provare "apt-get -f install" senza pacchetti (o specificare una soluzione).

``` 

Nothing changed. 

I also tried to install the missing dependencies but still don't work 
```
 
 lorenzo@mediaserver:~$ sudo apt-get -f install linux-toolsLettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze
Lettura informazioni sullo stato... Fatto
Il pacchetto linux-tools è un pacchetto virtuale fornito da:
  linux-tools-virtual 3.13.0.32.38
  linux-tools-lowlatency 3.13.0.32.38
  linux-tools-generic-lts-trusty 3.13.0.32.38
  linux-tools-generic-lts-saucy 3.13.0.32.38
  linux-tools-generic 3.13.0.32.38
È necessario sceglierne uno da installare.


E: Il pacchetto "linux-tools" non ha candidati da installare


lorenzo@mediaserver:~$ sudo apt-get -f install linux-tools-generic-lts-trusty
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere questi problemi:
I seguenti pacchetti hanno dipendenze non soddisfatte:
 linux-cloud-tools-3.13.0-32-generic : Dipende: linux-cloud-tools-3.13.0-32 ma non sta per essere installato
 linux-tools-3.13.0-32-generic : Dipende: linux-tools-3.13.0-32 ma non sta per essere installato
 linux-tools-generic-lts-trusty : Dipende: linux-tools-generic ma non sta per essere installato
E: Dipendenze non soddisfatte. Provare "apt-get -f install" senza pacchetti (o specificare una soluzione).
lorenzo@mediaserver:~$ sudo apt-get -f install linux-tools-generic
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze
Lettura informazioni sullo stato... Fatto
È utile eseguire "apt-get -f install" per correggere questi problemi:
I seguenti pacchetti hanno dipendenze non soddisfatte:
 linux-cloud-tools-3.13.0-32-generic : Dipende: linux-cloud-tools-3.13.0-32 ma non sta per essere installato
 linux-tools-3.13.0-32-generic : Dipende: linux-tools-3.13.0-32 ma non sta per essere installato
E: Dipendenze non soddisfatte. Provare "apt-get -f install" senza pacchetti (o specificare una soluzione).

```

Do I need to rebuild the kernel? And in that case which is the correct procedure to obtain all the packages and all the dependencies that I will need after the installation of the updated kernel? 

Thanks a lot for your precious help 
Lorenzo

---

### Post by lorenzo9 on 2014-07-28
Sorry. I didn't see your answer. I'll try it in  minute. Thanks!

---

### Post by lorenzo9 on 2014-07-28
It works! 
Thanks a lot! &#55357;&#56832;

---

