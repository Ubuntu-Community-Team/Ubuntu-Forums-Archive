---
title: "Someone can tell why I get error for permission of key when I download code?"
date: 2022-08-02
forum: Virtualisation
---

### Post by mm11751 on 2022-08-02
```

First I downloaded key file include id_rsa an id_rsa.pub from other OEM supplier
Then I wirte below:


[LIST]
[*][FONT=&quot]unzip -n sd-key-x9.zip -d buildsystem
[/FONT]

[*][FONT=&quot][RIGHT][/RIGHT]
[/FONT]
[FONT=&quot]cd buildsystem
[/FONT]

[*][FONT=&quot][RIGHT][/RIGHT]
[/FONT]
[FONT=&quot]chmod [COLOR=#006666 !important]0400[/COLOR] ./id_rsa*
[/FONT]

[*][FONT=&quot][RIGHT][/RIGHT]
[/FONT]
[FONT=&quot][COLOR=#4F4F4F !important]eval[/COLOR] [COLOR=#009900 !important]`ssh-agent`[/COLOR]
[/FONT]

[*][FONT=&quot]ssh-add id_rsa

[/FONT]
[/LIST]

```

After that I get error message:
[IMG]https://s3.bmp.ovh/imgs/2022/08/02/c53e1afeed64b69e.png[/IMG]

But I watched id_rsa.pub was this
[IMG]https://s3.bmp.ovh/imgs/2022/08/02/5e6e7680bd40d168.png[/IMG]

[LIST]
[*][FONT=&quot]unzip -n sd-key-x9.zip -d buildsystem
[/FONT]

[*][FONT=&quot][RIGHT][/RIGHT]
[/FONT]
[FONT=&quot]cd buildsystem
[/FONT]

[*][FONT=&quot][RIGHT][/RIGHT]
[/FONT]
[FONT=&quot]chmod [COLOR=#006666 !important]0400[/COLOR] ./id_rsa*
[/FONT]

[*][FONT=&quot][RIGHT][/RIGHT]
[/FONT]
[FONT=&quot][COLOR=#4F4F4F !important]eval[/COLOR] [COLOR=#009900 !important]`ssh-agent`[/COLOR]
[/FONT]

[*][FONT=&quot][/FONT]
[/LIST]

---

### Post by mm11751 on 2022-08-02
And I download another code from the same server is ok, this was strange?

---

