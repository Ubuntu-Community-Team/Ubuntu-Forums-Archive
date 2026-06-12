---
title: "SSH login (Password Less)"
date: 2017-08-08
forum: Security
---

### Post by sheenlim08 on 2017-08-08
Hello Ubuntu Community,

I have recently started to learn linux and chose Ubuntu for my starting platform.

I am trying to create a ssh based password-less login on my 2 servers.

Server1 - Ubuntu17.04
Server2 - Ubuntu17.04

On Server1
I have created a key-pair
[IMG]https://l0juxq.bn1303.livefilestore.com/y4mGPD7-WvcOVsk_TAW5WkrASd2PD0OgHNdeHO3VA6nHmNLsCpJoMrns7sks7rFCkOjb_4_FNCJx3RFVf3yVGlMt5y14PW8i2tnG_HKdkfyOJ8IKGaF0W5oMJ9hnaGmgThll8YY4pW-wbi7WxRorwF4S5VoFfgCdSvh3gaAsCDKbIex70Hlx9-NR8Xoe96R4Zrbx4R0ZU8CMh5qexBKHhOs6A/ssh1.PNG?psid=1[/IMG]

Then I export the Public Key to the remote Server. (Server2)
[IMG]https://l0jtxq.bn1303.livefilestore.com/y4mkCUAcbUhbaMljQbaRvlom4NrRRE_9DligXVAyDX5CGkdYW-4hjUIkqgcGxdYKUOhKFtJd6PBd-P5vrxFlZB2oWe9inKpFzrb985_hWR80K3VwWY5YcRxxGsL2qnVAFC0XiF2uA9OG_dWKtdsCmZ1uSYk1Qv-PPTAQV88nU_GDQvwf8ldROLDnEcCy5PQHWF6bebwwNM68qD9qrrvmUR0Cw/ssh2.PNG?psid=1[/IMG]

From Server2 I can see the Key being added to the /home/sheenlim08/.ssh/authorized_keys
[IMG]https://mej2xq.bn1303.livefilestore.com/y4micIroOHnF_P_qgZuH-uoWlc7_9b-GRe6JbEEnRF7274e15AzlWWgkbg6m-Fol4235yeLscM0_GHzyg7GOmhnzSlB7GFz4yfdYSuywq0klUINhu34dgBlkPYr9sKnUwj-SsnxDiuEg_JMI__UdvsCsGonFBPxehllgWmM_YY5rwB44c5_xySnfzAPoDf8vTAFIQxegMTHXc8NKdoz9-90Xg/ssh3.PNG?psid=1[/IMG]


However, when I ssh to 192.168.114.148 (Server2) from Server1, it still asking me for a password.
[IMG]https://mej1xq.bn1303.livefilestore.com/y4m-lIPPQZpCKNmvhwjL1_zHKboKj7e1Y1UcUZ7MAFbhtIS2mtIbgLjKXjVKZv9GkhwesJAAhCnbNbGh1Yx9KxeHmsS8jVfL7xPv0aioX42VZlsbHOrS3m9Wpm0muE580RKQN-LeXypazuoqxzi0UTbrYbmDeY2xiS_PkBfCc7xp4pug72K-ieaHDldp18-AaB-mOdEY6awJy8_Dh47PJFCGA/ssh4.PNG?psid=1[/IMG]

Any ideas?

---

### Post by sheenlim08 on 2017-08-08
It looks like i had to provide the identity file which is the private key. Lol, sorrry Noob here.! So for those who are asking how to do it.

[IMG]https://mej4xq.bn1303.livefilestore.com/y4m3ogrwz9MOu39l_OifekipaZt9fxgvlQtWukVhls4ZBrCrZqG_HzQNpD18E0LCou6J4l5rqVWFbBCkIyK5Su5rtp2QWorzsLMYiYrZIq8NOyTQz8FohvAdqqtgcIdHtFlzJeoP3-ASK-0SFCpgEc2zBTEB_U1yj1B3yRWJ2Pm80HalqVoqm0nSUKn1en9mJSi8Md2eK49Hc_QK_dICTQHAA/ssh5.PNG?psid=1[/IMG]

---

### Post by TheFu on 2017-08-17
Use the **~/.ssh/config** file to handle different key files for different userids and/or hosts.

If you hadn't picked a non-default name for the keys, it would have worked.

Another tool to make life better is **ssh-copy-id**.

Also, RSA isn't the best choice anymore.  Use stronger encryption - look at Ed25519.

Lastly, passed time to update that system.  61 security updates?  I'd freak out.  PATCH dude.

---

### Post by hbudman56 on 2017-09-05
stop the password and stop from leting the download

---

### Post by hbudman56 on 2017-09-05
let the password go way ok

---

