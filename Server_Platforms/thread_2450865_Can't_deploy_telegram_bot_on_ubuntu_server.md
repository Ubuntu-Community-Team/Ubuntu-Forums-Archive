---
title: "Can't deploy telegram bot on ubuntu server"
date: 2020-09-22
forum: Server Platforms
---

### Post by kokoto on 2020-09-22
HI i've made telegram bot and trying to deploy it on Ubuntu 18.04

[B]Requirements:
[/B]firebase==3.0.1
firebase-admin==4.3.0
pyTelegramBotAPI==3.7.1
grpcio==1.29.0
requests==2.23.0

I installed this on server:
[COLOR=#333333][FONT=&quot]*build-essential*[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]*libssl-dev*[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]*libffi-dev*[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]*python3-pip*[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]*python3-dev*[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]*python3-setuptools*[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot][I]python3-venv

[/I][/FONT][/COLOR][COLOR=#242729][FONT=Arial]After creating venv, i go to **/etc/systemd/system/** and made [B]uba.service

uba.service:
[/B][/FONT][/COLOR][Unit]
Description=uba
After=network.target

[Service]
User=uba
Group=uba

WorkingDirectory=/home/kokoto/uba/
Environment="PYTHONPATH=/home/kokoto/uba/"
ExecStart=/home/kokoto/uba/.venv/bin/python /home/kokoto/uba/bot_bd.py

[Install]
WantedBy=multi-user.target

But when i'm running bot, i have this errors:


uba.service - uba
Loaded: loaded (/etc/systemd/system/uba.service[COLOR=#66CC66];[/COLOR] disabled[COLOR=#66CC66];[/COLOR] vendor preset: enabled)
Active: failed (Result: exit-[COLOR=#DC143C]code[/COLOR]) since Mon [COLOR=#FF4500]2020[/COLOR]-[COLOR=#FF4500]09[/COLOR]-[COLOR=#FF4500]21[/COLOR] [COLOR=#FF4500]17[/COLOR]:[COLOR=#FF4500]48[/COLOR]:[COLOR=#FF4500]05[/COLOR] MSK[COLOR=#66CC66];[/COLOR] 16h ago
Process: [COLOR=#FF4500]10282[/COLOR] ExecStart[COLOR=#66CC66]=[/COLOR]/home/kokoto/uba/.venv/bin/python /home/kokoto/uba/bot_bd.py ([COLOR=#DC143C]code[/COLOR][COLOR=#66CC66]=[/COLOR]exited[COLOR=#66CC66],[/COLOR] status[COLOR=#66CC66]=[/COLOR][COLOR=#FF4500]216[/COLOR]/GROUP)
Main PID: [COLOR=#FF4500]10282[/COLOR] ([COLOR=#DC143C]code[/COLOR][COLOR=#66CC66]=[/COLOR]exited[COLOR=#66CC66],[/COLOR] status[COLOR=#66CC66]=[/COLOR][COLOR=#FF4500]216[/COLOR]/GROUP)
 
Sep [COLOR=#FF4500]21[/COLOR] [COLOR=#FF4500]17[/COLOR]:[COLOR=#FF4500]48[/COLOR]:[COLOR=#FF4500]05[/COLOR] s307229 systemd[[COLOR=#FF4500]1[/COLOR]]: Started uba.
Sep [COLOR=#FF4500]21[/COLOR] [COLOR=#FF4500]17[/COLOR]:[COLOR=#FF4500]48[/COLOR]:[COLOR=#FF4500]05[/COLOR] s307229 systemd[[COLOR=#FF4500]10282[/COLOR]]: uba.service: Failed to determine group credentials: No such process
Sep [COLOR=#FF4500]21[/COLOR] [COLOR=#FF4500]17[/COLOR]:[COLOR=#FF4500]48[/COLOR]:[COLOR=#FF4500]05[/COLOR] s307229 systemd[[COLOR=#FF4500]10282[/COLOR]]: uba.service: Failed at step GROUP spawning /home/kokoto/uba/.venv/bin/python: No such process
Sep [COLOR=#FF4500]21[/COLOR] [COLOR=#FF4500]17[/COLOR]:[COLOR=#FF4500]48[/COLOR]:[COLOR=#FF4500]05[/COLOR] s307229 systemd[[COLOR=#FF4500]1[/COLOR]]: uba.service: Main process exited[COLOR=#66CC66],[/COLOR] [COLOR=#DC143C]code[/COLOR][COLOR=#66CC66]=[/COLOR]exited[COLOR=#66CC66],[/COLOR] status[COLOR=#66CC66]=[/COLOR][COLOR=#FF4500]216[/COLOR]/GROUP
Sep [COLOR=#FF4500]21[/COLOR] [COLOR=#FF4500]17[/COLOR]:[COLOR=#FF4500]48[/COLOR]:[COLOR=#FF4500]05[/COLOR] s307229 systemd[[COLOR=#FF4500]1[/COLOR]]: uba.service: Failed [COLOR=#FF7700]with[/COLOR] result [COLOR=#483D8B]'exit-code'[/COLOR].

---

### Post by EuclideanCoffee on 2020-09-22
Did you create the user and group uba on your system?

Edit: Nevermind. It appears it's your home user. So it should exist by default. I don't see the reason why you need to set your user however in the systemd profile.

---

### Post by LHammonds on 2020-09-22
Make sure the user and group exist.

Are the user / group permissions correct in all the paths and files?

Have you tried manually running the script as that user?

LHammonds

---

