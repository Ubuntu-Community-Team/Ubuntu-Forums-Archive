---
title: "do i have midi prerequisites?"
date: 2010-04-27
forum: Ubuntu Studio
---

### Post by zander1013 on 2010-04-27
hi,

how can i tell if i have the midi prerequisites (hardware, ect)? i am using a laptop so i might not. i have attacked a screen shot of patchage with a fender gdec connected through its midi ports to the usb on my laptop.

otherwise how can i get started using midi with ubuntu studio?

please advise.

---

### Post by Fluxburn on 2010-04-27
Better then my luck, also tried as sudo

...@ubuntuMusic:~$ patchage
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_init: could not connect to server 'localhost' - disabling LASH
Failed to connect to LASH.  Session management will not occur.
Loading configuration file /home/fluxburn/.patchagerc
Unable to load file /home/fluxburn/.patchagerc!
Connecting to Jack... could not connect to jack server.
terminate called without an active exception
Aborted

---

### Post by zander1013 on 2010-04-27
perhaps its a dumb question but are you using ubuntu studio?

[http://ubuntustudio.org/](http://ubuntustudio.org/) i used to get errors like that before i realized ubuntu studio was its own distro with the real-time kernel.

i would try to install stuff like jack before i realized ubuntu studio was its own distro but it would crash with errors similar to yours.

my question is mainly about my sound card. how can i poll my sound card to see if it will play midi stuff (because i am on a laptop)?
:guitar:

---

### Post by sgx on 2010-04-28
Hi, after rebooting, try starting jackd with

jackd -d alsa -r 441000

Then start patchage, or qjackctl

you'll see your sound hardware in those interfaces,
and will need some experiments while you connect, so cable
an external audio device into your line-in, so you'll
hear when you make the right connections.

then start an instrument like zynaddsubfx, and connect
it to your sound system in one or both of those two gui.

Virtual midi ports were discussed recently, these commands
yielded 4 virtual midi ports to experiment with

sudo modprobe snd-virmidi
sudo amidi -p virtual -d

they'll pop up in your patchage/qjackctl gui

cheers

---

