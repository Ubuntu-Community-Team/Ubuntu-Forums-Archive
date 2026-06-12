---
title: "new Ubuntu Forums Dark !!!"
date: 2009-04-03
forum: The Cafe
---

### Post by tjwoosta on 2009-04-03
ok so ive been waiting for someone to create a darker skin for the ubuntu forums for quite a while now, but it seems if i want something done i should just do it myself ;)
 
so i finally got around to it and made a custom userstyle (for the stylish firefox addon)


if your interested you can use it by installing the stylish firefox add on and downloading the style here (just click load into stylish)

[http://userstyles.org/styles/16624]("http://userstyles.org/styles/16624")


ill admit, its not perfect, but i think its much better then any others i have tried


enjoy!

---

### Post by smartboyathome on 2009-04-03
Been shown on here before. I don't use it, though, because my computer has a light theme. ;)

EDIT: Nevermind, I was thinking of another skin for UF which was dark, also on user styles.

---

### Post by Skripka on 2009-04-03
I never use dark themes-they tend to be very hard on the eyes.

---

### Post by tjwoosta on 2009-04-03
> **smartboyathome said:**
> Been shown on here before. I don't use it, though, because my computer has a light theme. ;)

EDIT: Nevermind, I was thinking of another skin for UF which was dark, also on user styles.

yea it was probably the one that i modified to make this one

it was a bit lighter and used blue instead of the ubuntu colors

---

### Post by ninjapirate89 on 2009-04-03
I just tried it. It's a good start and it fits my desktop theme, however some of the fonts were a little too difficult to read so I am switching back.

---

### Post by jryprt on 2009-04-03
works with windows to

---

### Post by hessiess on 2009-04-03
> **Skripka said:**
> I never use dark themes-they tend to be very hard on the eyes.

Personally I find the opposite to be true, Darker themes (not black) are easier on the eyes. Nice theme btw.

---

### Post by tjwoosta on 2009-04-03
> **hessiess said:**
> Personally I find the opposite to be true, Darker themes (not black) are easier on the eyes.

i would tend to agree with this, however i will admit that certain aspects of this style are a bit hard on the eyes  (like when replying to posts)

like i said in the description i did not originally create this, and i dont know a whole lot about styling, i simply modified what was already there

if anyone can make it better please feel free

---

### Post by tjwoosta on 2009-04-03
speaking of which

does anybody know how to change the color of the input boxes ?

or the weekly reminder box at the top?

or any of this other stuff that i have pointed to?

---

### Post by ninjapirate89 on 2009-04-03
The reasons you just pointed out are the main reasons I switched back to default. If anyone gets these things fixed I would switch it back again.

---

### Post by wolfen69 on 2009-04-03
thank you very much. i've been waiting for someone to come out with a new dark theme. the regular bright theme is too bright at night time.

---

### Post by Sand &amp; Mercury on 2009-04-03
Nice idea, could use some work. If it matures a bit I might keep it.

---

### Post by hessiess on 2009-04-03
Hear is a some code which I use to change the colour of HTML forms in my personal generic `get rid of white backgrounds' theme.

```

  input, select, button {
    background: #888 !important;
    color: #111 !important;
  }

```

---

### Post by tjwoosta on 2009-04-03
well i still didnt figure out how to change the background colors that i was trying to fix, yet, but i did figure out that if i change the text to a slightly darker color it makes everything much easier on the eyes then before

i would still like to change those background colors though if anybody has any ideas

---

### Post by Sunflower1970 on 2009-04-03
Cool. Just installed it. Not bad. Not bad at all. Think I'll keep it for a while :) Thanks for making it!

---

### Post by tjwoosta on 2009-04-03
> **hessiess said:**
> Hear is a some code which I use to change the colour of HTML forms in my personal generic `get rid of white backgrounds' theme.

```

  input, select, button {
    background: #888 !important;
    color: #111 !important;
  }

```

hey thanks

im still not quite sure how all of this stuff works, but im slowly learning

that code seems to make all the input boxes grey except for the reply box


edit: ok i just updated the script with the new input box code

```

/****UbuntuForums.org Dark****/
/****Originally Created by: Sasani07 ****/
/****Modified by: tjwoosta ****/

@namespace url(http://www.w3.org/1999/xhtml);
@-moz-document domain("ubuntuforums.org") {

body {background-image:none !important; background-color:#3E3E3E !important;}

.tborder {border:0px !important;}

span.forumhome_stats {border:none !important;}

.page, .vbclean_topfg, .vbclean_top *, .vbclean_bottom *, .alt1, .alt2, .tborder, .alt1Active, .pagebody, .tcat, .vbmenu_control, .ubuntu_quotebackground, .panelsurround, .panel, .vbclean_bottomfg, .tfoot, .forumhome_stats, .vbclean_postbitmsgfg, .vbclean_postbitmsg *, .vBulletin_editor {background-color: #262626 !important;}
.vbclean_bottom *, .vbclean_top *, .vbclean_postbitmsg * {border-left: 1px solid #262626 !important; border-right: 1px solid #262626 !important;}

.alt1 {border-bottom:0 !important; border-right: 0 !important;}
.vbclean_postbitmsgfg .tborder tbody td {border-right:0 !important;}

.alt3 {background-color: #3E3E3E !important;}

.vbclean_postbitlegfg, .vbclean_postbitleg *, .alt4 {background-color:#3E3E3E !important;}
.vbclean_postbitleg * {border-right:1px solid #3E3E3E !important; border-left:1px solid #3E3E3E !important;}

.vbclean_forumdescfg, .vbclean_forumdesc * {background-color:#3E3E3E !important;}
.vbclean_forumdesc * {border-right: 1px solid #3E3E3E !important; border-left: 1px solid #3E3E3E !important;}

.vbclean_postbitlegfg .alt4 {border-bottom:2px solid #3E3E3E !important;}
.vbclean_postbitlegfg .alt3 {border-right:2px solid #3E3E3E !important;}
.forumhome_stats {border: 1px solid #3E3E3E !important;}

.vbclean_navbar_bg, .vblcean_navbar *, .vbclean_newthreadfg, .vbclean_newthread * {background-color:#3E3E3E !important;}
.vblcean_navbar *, .vbclean_newthread *  {border-right: 1px solid #3E3E3E !important;border-left: 1px solid #3E3E3E !important;}

.tcat {border-bottom: 1px solid #3E3E3E !important;}

.thead, .vbclean_fhomecatfg, .vbclean_fhomecat *, .vbclean_fhomecatfg .forumhome_stats {background-color: #3E3E3E !important;} 
.vbclean_fhomecat * {border-right: 1px solid #3E3E3E !important;border-left: 1px solid #3E3E3E !important;}

.ubuntu_quotebackground {border:solid #3E3E3E !important; border-width: 1px 1px 1px 7px !important;}

.thead {border-bottom:2px solid #3E3E3E !important;}

.vbclean_fhomecat_topfg, .vbclean_fhomecat_top *, .vbclean_fhomecat_topfg .forumhome_stats {background-color:#3E3E3E !important;}
.vbclean_fhomecat_top * {border-right:1px solid #3E3E3E !important; border-left:1px solid #3E3E3E !important;}

#navbar, .pda, .posttop {background-color:#3E3E3E !important;}
.posttext {background-color:#3E3E3E !important;}
.post {border:1px solid #3E3E3E !important;}

/**TEXT**/
* {color:#8A8A8A !important;}
.smallfont span, *:link {color:#796646 !important;}

/**INPUT BOXES**/
 input, select, button {background: #3E3E3E !important; color: #8A8A8A !important;}

/**IMAGES**/
img[src*="images/misc/ubuntulogo.png"] {width:0px !important; height:55px !important; background:url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAM4AAAA8CAIAAAHWICIXAAAABGdBTUEAALGPC%2FxhBQAAAAZiS0dEAP8A%2FwD%2FoL2nkwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9kEAxEIJPfuSfcAAAAZdEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIEdJTVBXgQ4XAAAaxUlEQVR42u1de5QcVZn%2F6tajq%2FpV3T09Mz3T84RMTyAgggEkulnARTcaYM96cEGOD1yWhXXBxfjA3ZWHsOrRjbriWSGwuruRAwdEV04UJRgVj6JGQeQRpmeSSSbpmZ6enn5Xd3VX1a39407u3Knu6enMTBII8x3O0LlVdeurW9%2F9vt%2F3uLe4C2MdWQjAKhGifX1yID3ypviueNxjWcvvjvxvzx3jXz4Y%2FouRwaHrYcfGydavj8fjzu4%2BOZAm%2FzhcFYeficWCVcfZExMT9LKJiQnSTloQQvS0TCaDAOD6voyJ5%2B8wfR92sNDX1%2Bfz%2BQAA47lDwWAwEomwLQDA8zwCgOFnYgICALBte1c8PiVKlLWenh7yQ5ZlABgbG3O5XADg9XpJCwCkUqnYUCwej6uqysViMdJ6eyJxgab1%2FJB76yfW6Ra3vFcx392q0Cp3h%2BivkTfFAWDXwhe%2FzO5Gvhn%2F0MGer6yf8n9EaC5ZS3S3pa14xXmF4Ztivym4P%2F5qV2fBvDio0V7K5TIA1Go1jDFpGRsbSyaT6XSaCKDjruhr66aeeM5PW1%2F9LhgT86JEpFSSpCNHjtDGQqEQDod1XW%2FA3fBvY%2BRhz6hUP5ac5gF%2B5fMBwOmnn07ELRaLxePxvr4%2B8mPdunX1TMXj8a6urgVvdlc8vjUW23PH%2BKV3DbYyTIVCwe%2F3k78nSe7IVNm6qrdsnRYImczbusWNvDNeMBEA%2FPCQHydaVXrLG7PmF84zN3J%2FPDEphgLm8K3zZ3si1s8vG98LY%2BfvWVffI9t1LpdLpVI9PT1ut5s9lM%2FnLcsKhUJEkeVyOZ%2FPR2SKitjQ0BDHcWy3g4ODoigiAHh5y%2BjeS8fOumFDNGK8%2BdYhlneN58%2Ffs47lzEFkCgJAIBCIxWLZbNYx8%2FL5fCaTIbe0bTsWiymKQtgirMRiMY5z6tZisTinTTY8OXT%2BnnUv7Xg5kRSf%2B%2BoYexJR9fUaa2JiYmZmBgDIOAFAMpkEAE3TiP0g3Giaput6e3s7O%2FvJ34Yacnx8nDxJMBh0ToioaiTyImXFArjyOEwFxwxf%2FmwduTee1fhNtw1hwMeJv0KhAAAN2V1lzXRcrGFD2hWPn6bjk8KZc8x6XcbTfz4OSYAS%2FH63W7XKAHBS1C9yCNbhqlgwUSGMzGHu2qE%2BAPjI4LrmXczMzIyPjy%2Fj3plMJp%2FPL614f%2FfV%2FYm0KNv2A6%2BGHk%2BqZ6v6yMCrvz9H%2BaU0Rmz4YlSr1QzDWAZnRCerqrrEmJVyCAB0jtsxGZrF%2FM%2BznuEDsY2%2BSsGDnnn7AXpaIpGoVqsOBIUQogib8Ep1L220bZucQzBzpVIxDIPCpZmZGaJp5yESADx07mEACAVMQbEdjJ%2F5iyEA6DTMeQuhaUQrUktAAHp%2Ff78oiqTTXC5XD6BGR0cRQrIsj42NAYCiKKIoiqJIBD2bzU5PTwOAac7dS9i9aTwgWyOb49%2F%2BWbBqOC2GxXFNzNQ8OJBll8s1ODjYHIcSpBaPxy3L4nkeAKzFvTH0kT%2F0%2BAW8fSx89SW5yy8oOo%2FbsCse%2F8HC%2B5HXQR2ZBmanroX1etiBaXIOOlwVh5%2BK7ZgMZXJCA302GgcAYKyv3%2B%2FXNK1cLk9OznmLqqqSdzc1NUVawuEweaetz9mOjg4iKgcOHHDOgGi3AQCybb83kwWEzirr1IxeOTQPRiKRiCzLBJkTEXG73cFgMB6PF4tFqh07OztTqZRhGKTFMYrE8evr66MzIBAI%2BHy%2BRCJBu12gaUfujQ%2FfHKMM3d098HxIrNW4k2%2Bdhm%2BOdRiYwo13X5f98WcOjnwzvor3Iya84W9CjfE3AKRERG3RFfsLF60vn%2FjRImDktYs1XrucvZZJaP1U2bY9PNYNsBDSOe5jyenLCvl5fL5%2BPWC8NmpzdEN3Ztu6dEGY1zF%2BAQ8%2FFauieV3HrwYrtVpNkqTX8ajxtv3KfaOA4JGn1Tse69xbVB458zC4AAg8c8HI5viDE6GtB2OAEGB8rq8CxRUJWiKR0DSNGqgTQGNjYwRJLOOODUbt2k252z%2BQSiRFALh8U3HjcOU99wzUA%2B%2BYq0qjNgDgN%2FHVz%2Fc%2BX1Qa38cGaMEM18OoVsi27fqYxJJEgCL5e6wdOq1BVDX2fHGcDFk0Yrz%2FS71%2FGFeaXP%2B%2Bzvzd50yTsfNreNPe02cx3zD06vF4otEojd4QREWDSlTWHBQOh0mACQCmp6eJ10WCSjQ6Qjwl9kEagmx6VbFYpKCSRd5stoDt0DAMAjkpM8Lckw9MmyFOsOy8xg%2FfFPvhvx70SfiRPWrzIQOAR6fVwEuWKmEA8PD4bFX%2FedazEjlyPHw6ncYYE8BMR4oVBJ7nDcNgOyePLYri4OAgO%2F1HR0dJ5z6fz%2BfzkeFGCDliyvXc1ssdAoAruwtmiCtXuYKJ1KKFAP1%2BRPH7Ws04VV%2Bwi7%2FDxd%2Fh5LNQOLIiXePxLBhxElyjXmkr05A6PV6vlzaS3BExOCuCaUcZEADg2ud7AeBcX%2BWlgt%2FgjEe3HYyoZiYnXH1p%2FtFfqS9Pyk06uiyfvyo7S%2FHHw23hhu8NY8xOQPqbpqpEUSSOPHthNptlh5KenM%2FnaQyCuHEtGl%2Fbnnf9F3N9RVEkwYT6aLCiKIui3BsuzfzD5bPEIQ0FzMSs%2BJ57Bhr4jAb%2B1viCeO9tPX0vueWG75%2FEEBxElRoNC9dHIWiknFA6nSbRjMXmtWVZ%2B%2FfvJ44j8WrJKJNgRV9fHx36ek1KO2moFjs6OgKBQDPfICRbz355P0hzyOM0HX91Yow%2FKlAUoI3Iyp8Ud8AyLyvkW4wI0ijHkhLRfD7atm3b9mK6EmPsOLSYWVy6Hw7VW%2F%2BlPaqtudyNqZSj8dvh9sdDwZH741ADANj%2B%2FfCOPaHXJiJtPQFwHPxQhGTL4jEGAItz6ch8dNtERDVNiyNRnEs%2FNZjIi6%2FlUXMMX%2FN2R1J1NbOrV5xX%2BPt3Z0aPuG7bGVl2XcHrkdZiHmujdlKipWu0%2BvE1B52naZ9LJABgVyBw31Fk9AYhvq2traXzbBRUTDe2FZddMREg9MDRHEpM16sc2qcoa7I2P4E3B7W%2FG8hslCpAvJ0SbNfDTx9YUHX5wdn046Hg2qjNkWTb9wcTZoQrVBF4AADcUfv8RGVHcoG%2F%2BcDRspdlk23blmUJgvC6GLVFrcFdV03fuiWtc9w%2F5bsEa97pLVe5zRENMP5kbz9p2e1XdwUCKxyy0dHRAwcOsLny40okz9nQO16%2BrN26JX31pXkA%2BI8nO56c9X2mPNOJTKDlwCq8vGX0z3522lbPesLCxUFtsbBaK0QDOLqus%2F788SPit2OMK5WKcuwaucGoXbJBu%2FHdmUOTot%2BDv%2FWPEx%2F%2BRs%2F1e6MXt2lPzvrKBmoTzYvbtG1npZ%2BN7Z%2FwiqmKsNFXgRxsyjeI4h5r3OrEExs7WtEMve%2BWxKGUKCAoV9BFw%2BWoasSrrh2TocNVcRbz5PfwU7GHtUCf14gFqwUBFcLomXcdOAHsgr06g0XfU4sRZge3Qr1rWSlzJI0XCpife7hjMZ%2F8zv0dEsJXriuWqxwACJodc1XjVZfjtGq1eujQIVmW%2B%2Fr6aCMJeLW3t5NoLSXDMGjYy%2BfzdUW62CgNOdTb28vOKbYUdF75lsuTk5M0stjd3c2GdmnsG44uNKAnmKZJSkxiQzF6a5LlYPMezpH%2BxPvSenWuMTErPvTrZmr%2Bn0cjgjb3EkwP9%2F6efMOQAxyNuFIikUVSmspEVVA%2Bn6eRwmKxGB%2BN1yujXC5HW2jsl0bJSedHjhxhg7GTk5MpJthVX8dG47r07np1nmESUtY0bb5IiSDYzw8lH3hT4q3%2B8ubbTiMHohHj6z8ILym628fCbpdNbOs1p%2BdWPnc6OzsHBgZoGLY%2BmdR8TlmWlU7PLWpRVZVGX3O5HC22i8Vi3d3dGGOMcW9vbywWq6%2FpY1UtveOCvMEr73rV5DkA2Kxol%2F%2Bx%2F2%2B%2FHv3eZycA4Ok%2F%2BYFbIjf85KyvO25qFgKAoGiS6vZlo4FQKEQeQJIkwzCy2WyxWGQj4EsSFbpIJEIiYoFA4ODBg0TqaTk11VPLU6%2FCub4K5KHs4QAAPNwdZ6ZI8gUALG7pdPrhqnjn%2FlVzQmkyiUgKmRqGYZBczDGBGBpElCSJpHscqZwV%2BQbpmgAVmMP9Lnu04GLsK1qy2ru3Zvx1JkNqPlzYvr%2BzQ18BjGDnhXR0QZZpmuyoNZQOeuEyTXOL7B01EOhwVXxYC%2FhN7BewoNl37u%2B44dJMRecA4LKzC0t2dEGpdFkhvzWX25rLXVbI1w9Zk9xKvb5gn9kwjYY9sBk5ej7taoWjRu%2FVuB%2BOQR537u%2B4d7ytTTTjVdeGbn3bVWlSsXDLlemfvOhtivbQdel5O7jb36BOmrqWbOidWDGaxBQFkdp4UtzJmjN6Wv1Eo%2Bcoy424OAA25bZUKtEcIGugFyAPAl8B4M0DOhE0AIi2GdduamYWb0wm2X8%2BpTaAKTQHnEwmc7mcpmm0TJcaOODmssgzMzNEMem6TrACZZ1qPYzxxMREuVxOp9NE8S3Du6CySd4BrV2WXTKFL%2Bl0ulwu0xJ2Wm7SAK899OuAIttk%2FWgmJ9x%2BTSqqNq7SvzGV2ppbMKb7PEpDmadQNpVKJRIJImgIITbr093dTX4cPHgwHo9TXimwJKCEuqtHjhyh6WR67WIzi%2BAsdmpTRZlOp%2BPx%2BIEDB%2BaKbjmgC5kI7qNIk9SaLBqVHJ1wXbM5XyzzAm%2B%2FOCHv%2FGWwt2ZcWCpNi6IhCB01a1Op8G%2BJqbMr8%2FEJC%2BCjA4OFRZCUx%2BPheZ5NdKuqyroKZGp4PJ5yuUyRpCzLvb29jthRIBBwLLfo6elhq0NIaYQoiqzXUavVarVaIBCgoQGe5zmOY0Ms7e3tRKm5XC6Xy8XOSp%2FP19%2Ffz4pz42zLXVdNk5jHGTetx4Af2n9EtcoWAA9gMZWRu%2F1qjhfeXir%2BWFVbiUo2T3SzT77kOU1y%2BA0PLXa%2BZVk84herrVuMk8aRojse61Q9%2BNC0iAG%2FrVgkq5TIPcnfcZf75v4eAJAk%2B39qba2r3lYUUCsedRPT7DhErNBi5zcvn1iMkyUye6Itfnf05fqOt65ff%2B1bM7dfkyIjT0TyjRMBX2oicMY3OjstRkAsgHGXGzC%2B%2FQOpRFpMpMVsnv%2FKhxOvlwemSy3YNRf17Yut12gpb4ABdqvqblXlbVvGWADOBFtHYlSd3%2BehXEGbzim%2F7uRlsZIZ0s4erV9F32p2w%2BI4bV4F4EReBARuBRc01N9h3LKj%2B9Seko4hbjUfWk8PPhlaH62Kor39%2B%2BEfveB7vTw%2F9T1abF%2BONVij5ViDNWosa2fH%2BqvgWhuINTreJJwsOeutGesrZb%2BFASApCqOyJyWuaYtTWtRO%2FC3PqFQ%2FnpzqMGqsm2YBvKwoX4tE1wTulDWgqwLWeBuJYPXJtW632SGZAd5SJezhsYRwDSPNQvka2ltUni8qvTXj9kSiy2i8mGlKlG4e6Nc5bu3FrGk1J4Vk65bo7DWeHACAAuACkMHkOVL4QcjtsgXNfnAi9HxRqXK8jgSAxqKmI2HtlZyqtBzHPaoam2IVWcAzRaFiohfz8lBHrT9gmCpXslEVc8bCegXD4ngFemXj6WnvlC2MyN71uu63DLTQgL6kKHdHoxo6mQa0VqvNzMxMTk4WCgWe54%2FJm3%2B9kG3bmqaReGHr9Qwn2oCGZOuGd2au25IFE6Y14db7u%2Bji7s8PJd%2FbVTA98%2FqMVhnN6zbL3v5SeMdkCBASLf48TeupaQDwiuLeJ7vgZJtNImdsFo1dDXpqUKVSSSaTNL0nimJPT8%2BJEbhj0GrXbsrt%2FNSRc4f0Q5OiVuG7wuZfvqV0cFLan5IA4KcZb83g3m6VXbY9jYVXc%2FIrs66XZ12Tmlg1kZu3%2FSaGNGxyl28enj3HX%2BkQqikXeiWoTCpSb8i4KlK468zpm%2FsyL%2BblI9WTs1TSsqxyucxmWRVFUU6tZSe6rheLRTbJ7vF4ToyotaTVZN6%2B76bERRvK2Txf0BDddCfabQCG7Y%2BF%2F%2BunQZK%2Fkm27xvGLZffakPWO9tKV3YWNUgUA2DCL6Tlafpiwt6fDD06GT3yKsF6rsbuInBpUKpVmZmZYrdbV1cUW0ZxMtyAkW%2Fd9NHHOOp1UZQkslMIACDQdiQKQihOd42BxEZnF%2FKPT6qPTqmzbNw%2FOXt%2BXARnmtuo5miB0R2GbklYlfO94W%2BuuaK1WI9Ursiw32ZwCY6zrumEYgiAoitI8t0%2BPWpal6zopN%2BI4ThRFSZKW3OqAsGTbNtktshWWZFleslvLsizLMgyDlj8hhCRJEgSh%2BbWkxoVWtJBqNgAoFoukfEsURZfLVT8mpmlWKhWMsSRJsiwvVjRh23a1Wq1Wq2RDznpNuYRW4217%2B3XJLRcWs3m%2BXJlnQhLs9rD5yB71rse6lq1%2BYq7qHWemNvoqhQXyO%2Bexfnak8%2FFksJWKYFJhRv%2FJ7t%2FhsB2pVIqt3O%2Fv72eFgNVq9E00ofb29mAg2BBitshSrVZLJpMsS%2Bw%2BIw6JzOVybJ8NKRgMhkKhepkjm4c7ZhGp%2BGEf0%2Bfztbe3s9VbpVKJbhhKZnJ3d3f90kBScM%2Fu2EtryJthtTZkIdM2EAIAm%2BMkZF%2B4oRLwWsXS3AO4FdwWtr79o%2BA93%2B%2BwV7AwZ9YSXsrKMbU2qBlVN8d6rK6KHQ2Y%2BwpSsia2YhTYt8XzfMMShFqtViwWHSPLTj4Wq5GaJ4ppiCbjOM6x%2FU42lxUEoV5pFYtFliVJkrweb71QEjXD6idFURr2RmpCW4Fi2WyW9MO2ezweolw5jrMsC2NMno7jOK%2FX6%2FV6PR5PMBgMBAIOMa1UKiyiME3T5%2FM1FDVN09i9n2RZdqjAuWtk2%2F5gNLvtrDTk5yHUNBa%2BsK%2F9ief8Tzznv%2B2Kmeu2ZAlWC6rWsy%2B6d%2F5iFVyzeNX1nYnARrXiL2FgV%2BPOwDBUz%2FdV%2FlSQreXW2a6EiEjJshwOhx0LLovFYjqdJhKJMU6lUgghdm1WA0TMccv2rzVNcygzWZbb29sVWSF9GoYxOzvLFjvNzMwghByLdDwej8fjKZVK5FshdFoGg8HWsRpCqKEBbaUUUSBq7ItnJTeDBgAFz%2Fx7anNZX4tOneWrfvlg%2BItPtEdC5pYLi0HVAoAX9surtaXOT2bVc9JeADD2g81xAMDZtgjg4bFmIfvkZQ5IPW%2F9wl6fz8dxXDKZpFtlF4vF5qK2wvAE6xR7PJ5IJMLqHlEUI5GIIAjsBmGlUkn1q%2FXyTfU0LerGJ2qzWQQAQ97qsL8KCtDNNOcMRJWDAPxZpyZjAQAOTR8XlxgD5jF2YVu0Rd4WeVsUAXiMTYMDe5XvuCTodpy8GJxXFIVd5KXresNP%2FiwnIrBwatm27RCFxTwSURRZdW5ZFl0OVG%2FsTsrUFQDgNwX3dw4EtvWm%2FRomO0pSbA4An9%2FXriMzqhoXnVkGgERSjEaMc07XyfdSVs7B24rFT9Wt%2BiT0v%2BH2%2FwsGYCnF1vpKFnaUV2Jnl6xedxzFGLe4H2397notap36zldFXS17DwKEEM8t8OnmHmzHZGjT3tO3Hw5P5ufQ2x%2BT8mdHOoefif2m4N7Qre%2B4eS7eYWLI5vmLNpTftymPVlwk2Fsz3lEoAAC%2F8D8ASInSK4q7FaDmQKmGYTScuKZpsu08zzsu5HmeVRiWZTX8FkS9GpMkyaH%2FHK4%2BG5twtLNQup6lk06CILDSjzFe7PsYjnXwPM%2FjxeJqs5jfMRnaMRlaaF%2FRVz6c2HJhsaJzNK5Goh43%2FlXGJdpfeqJz2cGO3ppx03RyQ6VSbw94gB8EA%2FvkllKQLpdLlmX67nVdTyaTHR0d7PsuFAqzs7PsRHe73Y4IHM%2FzsixTfE1WjLtcLofBqtVq2WyWFTWv1%2BuY%2FfUspVIpB0vFYtHBkqIoJ2C7eJ7nWbeg%2BcmSJHk8HnYR2dTUVCQSYbFpfRRJFMX6LMvS2YKQbO38xOF10RoRNZaiESOv8%2FfsbH%2FqBd%2BxbQmA0IemZ%2BhmxE4zB%2FBkILCzrU1rGVoVCoXkwqWprDGqNyVk%2BV9D6zAzM0MXmbIDR1fwOqbvYhmFUqlEXYcWWaoPWREPl%2FUug8Fge6OdswqFQiqVYtc3dnZ21mNNsorWIRZer5dsA16tVt1ut6qq7JTQdX1qaqp%2B8w4anKtnpmF0cGl1ndH5D%2Fx7L0kYTM8IusHNB1wRqLIVCZiGyUMLsVYZC2%2FRsu8oFC5otJc8lbPvBdv%2BOxw6JpTg9%2FsVRclms2ygsuEoiKIYDodZUF8fmPV4POz7MAyj4de%2BfD5fW1vbYnrI6%2FUODAxks1lWcBuyhBDq7OxsyBIb22sOnhwxP8uyGoJRt9vt9%2FtZUSPKmxUsSZJYUZNleWBgIJ%2FPpxbukdzwWdrb2wOBQOOASIuVHQjQ9Zemt12VBoBDk6KAIBoxNB195lsRunvAezNZslHAiKxMSFKOFwBAsa0Ow2g37cFq2SFSfJ2Q8QB3dw%2F81rsiI6Lreq1WI8iMxCoRQoIgiKLYSuaHheSVSoV0Rdb%2BchxH8JwkSceUhicZm%2BWxRKKjmqYhhHw%2BX5Nd1Ugq3TRNRVGaJ9GJeiaPRvkhSNHtdjfhh2g%2B0zTJhWQ9tCAIJKvWPG1%2FbEVEUdW44Z2ZqzfnARYWESF0YzLp2CdgMaWVEqUfq%2BrzbvWwy2XwFgDIJlqnl1TL%2BJXXB2sVuKcoLafgO6oaF2%2FQ%2FnhQJp%2BGUC386clEQ3TvoDzv%2FkJXmHzt4C2DlSs2Fs7oqwLAvgnXr1%2F17H7R%2F4Za8L1adDy2z3%2BtiBpLHQb%2B9FRinb60nBV58WN9%2FSkRXbJB2379lEfAMzmhZnIAIPB2Z7sJALf8Z%2FcSm%2FmsUZ2csYB1yXZgvjlADy32sYIm50Ojte70pg1Ff6VRnJSItvX1AgBv292G2VfVI4bZU6uplilj7LKhyoGOUEoUX1SUlEsIScaHLsl6ZDw9I5hHnVbT4hJJMdpt%2FMu1qb13KhmdX5Oh1v2heq3WXHSaSEPzG9GuWhHQ1Re1eRDGcYcl8bDUNH%2BAcb6CciUeAPw%2BK5URiDNrYpBFGzAcOCKVjbXFea9XoW8ucyc6Nm1x3G07I69MuLb9TbpfMFhG2GreNVq5qmtdgbHnLxv2LdnDydy0IyRbXSEDAKYy4prRPOXpZGbcMjqfmVyTsDcKrQGjNTpB9P93xGZwBc9tSgAAAABJRU5ErkJggg%3D%3D) no-repeat !important; padding-right:202px !important; z-index:1 !important;}

}

```

---

### Post by tjwoosta on 2009-04-03
bump

---

### Post by iaculallad on 2009-04-03
I still prefer looking at the the light colored Ubuntuforums, it's original color/theme. It just makes my day :p

---

### Post by wolfen69 on 2009-04-03
the only "issue" i have with it, is that when i type into quick reply, (or regular reply) the fonts are too light. they should be darker. then again, that could be because of the theme i'm using.

but anyway, thanks again for doing this. it's much easier on the eyes late at night.

---

### Post by tjwoosta on 2009-04-03
> **wolfen69 said:**
> the only "issue" i have with it, is that when i type into quick reply, (or regular reply) the fonts are too light. they should be darker. then again, that could be because of the theme i'm using.

but anyway, thanks again for doing this. it's much easier on the eyes late at night.

i agree, i actually wanted to chaange the colors of the reply boxes to a darker color but it still cant figure out how

btw i did update the script with a bit darker fonts since the last time you posted, its a bit better now

---

### Post by MaxIBoy on 2009-04-03
Looking good! It actually matches my theme perfectly!

Now, is there a way to replace pictures in CSS? Because that would be awesome.

---

### Post by tjwoosta on 2009-04-03
> **MaxIBoy said:**
> Looking good! It actually matches my theme perfectly!

Now, is there a way to replace pictures in CSS? Because that would be awesome.

there is a way im sure but like i said im still learning this stuff myself


the only picture i know how to change is the ubuntu forums logo at the top left

you just need to use a converter to convert your image into base64

[http://www.greywyvern.com/code/php/binary2base64]("http://www.greywyvern.com/code/php/binary2base64")

and replace this section

```

data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAM4AAAA8CAIAAAHWICIXAAAABGdBTUEAALGPC%2FxhBQAAAAZiS0dEAP8A%2FwD%2FoL2nkwAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9kEAxEIJPfuSfcAAAAZdEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIEdJTVBXgQ4XAAAaxUlEQVR42u1de5QcVZn%2F6tajq%2FpV3T09Mz3T84RMTyAgggEkulnARTcaYM96cEGOD1yWhXXBxfjA3ZWHsOrRjbriWSGwuruRAwdEV04UJRgVj6JGQeQRpmeSSSbpmZ6enn5Xd3VX1a39407u3Knu6enMTBII8x3O0LlVdeurW9%2F9vt%2F3uLe4C2MdWQjAKhGifX1yID3ypviueNxjWcvvjvxvzx3jXz4Y%2FouRwaHrYcfGydavj8fjzu4%2BOZAm%2FzhcFYeficWCVcfZExMT9LKJiQnSTloQQvS0TCaDAOD6voyJ5%2B8wfR92sNDX1%2Bfz%2BQAA47lDwWAwEomwLQDA8zwCgOFnYgICALBte1c8PiVKlLWenh7yQ5ZlABgbG3O5XADg9XpJCwCkUqnYUCwej6uqysViMdJ6eyJxgab1%2FJB76yfW6Ra3vFcx392q0Cp3h%2BivkTfFAWDXwhe%2FzO5Gvhn%2F0MGer6yf8n9EaC5ZS3S3pa14xXmF4Ztivym4P%2F5qV2fBvDio0V7K5TIA1Go1jDFpGRsbSyaT6XSaCKDjruhr66aeeM5PW1%2F9LhgT86JEpFSSpCNHjtDGQqEQDod1XW%2FA3fBvY%2BRhz6hUP5ac5gF%2B5fMBwOmnn07ELRaLxePxvr4%2B8mPdunX1TMXj8a6urgVvdlc8vjUW23PH%2BKV3DbYyTIVCwe%2F3k78nSe7IVNm6qrdsnRYImczbusWNvDNeMBEA%2FPCQHydaVXrLG7PmF84zN3J%2FPDEphgLm8K3zZ3si1s8vG98LY%2BfvWVffI9t1LpdLpVI9PT1ut5s9lM%2FnLcsKhUJEkeVyOZ%2FPR2SKitjQ0BDHcWy3g4ODoigiAHh5y%2BjeS8fOumFDNGK8%2BdYhlneN58%2Ffs47lzEFkCgJAIBCIxWLZbNYx8%2FL5fCaTIbe0bTsWiymKQtgirMRiMY5z6tZisTinTTY8OXT%2BnnUv7Xg5kRSf%2B%2BoYexJR9fUaa2JiYmZmBgDIOAFAMpkEAE3TiP0g3Giaput6e3s7O%2FvJ34Yacnx8nDxJMBh0ToioaiTyImXFArjyOEwFxwxf%2FmwduTee1fhNtw1hwMeJv0KhAAAN2V1lzXRcrGFD2hWPn6bjk8KZc8x6XcbTfz4OSYAS%2FH63W7XKAHBS1C9yCNbhqlgwUSGMzGHu2qE%2BAPjI4LrmXczMzIyPjy%2Fj3plMJp%2FPL614f%2FfV%2FYm0KNv2A6%2BGHk%2BqZ6v6yMCrvz9H%2BaU0Rmz4YlSr1QzDWAZnRCerqrrEmJVyCAB0jtsxGZrF%2FM%2BznuEDsY2%2BSsGDnnn7AXpaIpGoVqsOBIUQogib8Ep1L220bZucQzBzpVIxDIPCpZmZGaJp5yESADx07mEACAVMQbEdjJ%2F5iyEA6DTMeQuhaUQrUktAAHp%2Ff78oiqTTXC5XD6BGR0cRQrIsj42NAYCiKKIoiqJIBD2bzU5PTwOAac7dS9i9aTwgWyOb49%2F%2BWbBqOC2GxXFNzNQ8OJBll8s1ODjYHIcSpBaPxy3L4nkeAKzFvTH0kT%2F0%2BAW8fSx89SW5yy8oOo%2FbsCse%2F8HC%2B5HXQR2ZBmanroX1etiBaXIOOlwVh5%2BK7ZgMZXJCA302GgcAYKyv3%2B%2FXNK1cLk9OznmLqqqSdzc1NUVawuEweaetz9mOjg4iKgcOHHDOgGi3AQCybb83kwWEzirr1IxeOTQPRiKRiCzLBJkTEXG73cFgMB6PF4tFqh07OztTqZRhGKTFMYrE8evr66MzIBAI%2BHy%2BRCJBu12gaUfujQ%2FfHKMM3d098HxIrNW4k2%2Bdhm%2BOdRiYwo13X5f98WcOjnwzvor3Iya84W9CjfE3AKRERG3RFfsLF60vn%2FjRImDktYs1XrucvZZJaP1U2bY9PNYNsBDSOe5jyenLCvl5fL5%2BPWC8NmpzdEN3Ztu6dEGY1zF%2BAQ8%2FFauieV3HrwYrtVpNkqTX8ajxtv3KfaOA4JGn1Tse69xbVB458zC4AAg8c8HI5viDE6GtB2OAEGB8rq8CxRUJWiKR0DSNGqgTQGNjYwRJLOOODUbt2k252z%2BQSiRFALh8U3HjcOU99wzUA%2B%2BYq0qjNgDgN%2FHVz%2Fc%2BX1Qa38cGaMEM18OoVsi27fqYxJJEgCL5e6wdOq1BVDX2fHGcDFk0Yrz%2FS71%2FGFeaXP%2B%2Bzvzd50yTsfNreNPe02cx3zD06vF4otEojd4QREWDSlTWHBQOh0mACQCmp6eJ10WCSjQ6Qjwl9kEagmx6VbFYpKCSRd5stoDt0DAMAjkpM8Lckw9MmyFOsOy8xg%2FfFPvhvx70SfiRPWrzIQOAR6fVwEuWKmEA8PD4bFX%2FedazEjlyPHw6ncYYE8BMR4oVBJ7nDcNgOyePLYri4OAgO%2F1HR0dJ5z6fz%2BfzkeFGCDliyvXc1ssdAoAruwtmiCtXuYKJ1KKFAP1%2BRPH7Ws04VV%2Bwi7%2FDxd%2Fh5LNQOLIiXePxLBhxElyjXmkr05A6PV6vlzaS3BExOCuCaUcZEADg2ud7AeBcX%2BWlgt%2FgjEe3HYyoZiYnXH1p%2FtFfqS9Pyk06uiyfvyo7S%2FHHw23hhu8NY8xOQPqbpqpEUSSOPHthNptlh5KenM%2FnaQyCuHEtGl%2Fbnnf9F3N9RVEkwYT6aLCiKIui3BsuzfzD5bPEIQ0FzMSs%2BJ57Bhr4jAb%2B1viCeO9tPX0vueWG75%2FEEBxElRoNC9dHIWiknFA6nSbRjMXmtWVZ%2B%2FfvJ44j8WrJKJNgRV9fHx36ek1KO2moFjs6OgKBQDPfICRbz355P0hzyOM0HX91Yow%2FKlAUoI3Iyp8Ud8AyLyvkW4wI0ijHkhLRfD7atm3b9mK6EmPsOLSYWVy6Hw7VW%2F%2BlPaqtudyNqZSj8dvh9sdDwZH741ADANj%2B%2FfCOPaHXJiJtPQFwHPxQhGTL4jEGAItz6ch8dNtERDVNiyNRnEs%2FNZjIi6%2FlUXMMX%2FN2R1J1NbOrV5xX%2BPt3Z0aPuG7bGVl2XcHrkdZiHmujdlKipWu0%2BvE1B52naZ9LJABgVyBw31Fk9AYhvq2traXzbBRUTDe2FZddMREg9MDRHEpM16sc2qcoa7I2P4E3B7W%2FG8hslCpAvJ0SbNfDTx9YUHX5wdn046Hg2qjNkWTb9wcTZoQrVBF4AADcUfv8RGVHcoG%2F%2BcDRspdlk23blmUJgvC6GLVFrcFdV03fuiWtc9w%2F5bsEa97pLVe5zRENMP5kbz9p2e1XdwUCKxyy0dHRAwcOsLny40okz9nQO16%2BrN26JX31pXkA%2BI8nO56c9X2mPNOJTKDlwCq8vGX0z3522lbPesLCxUFtsbBaK0QDOLqus%2F788SPit2OMK5WKcuwaucGoXbJBu%2FHdmUOTot%2BDv%2FWPEx%2F%2BRs%2F1e6MXt2lPzvrKBmoTzYvbtG1npZ%2BN7Z%2FwiqmKsNFXgRxsyjeI4h5r3OrEExs7WtEMve%2BWxKGUKCAoV9BFw%2BWoasSrrh2TocNVcRbz5PfwU7GHtUCf14gFqwUBFcLomXcdOAHsgr06g0XfU4sRZge3Qr1rWSlzJI0XCpife7hjMZ%2F8zv0dEsJXriuWqxwACJodc1XjVZfjtGq1eujQIVmW%2B%2Fr6aCMJeLW3t5NoLSXDMGjYy%2BfzdUW62CgNOdTb28vOKbYUdF75lsuTk5M0stjd3c2GdmnsG44uNKAnmKZJSkxiQzF6a5LlYPMezpH%2BxPvSenWuMTErPvTrZmr%2Bn0cjgjb3EkwP9%2F6efMOQAxyNuFIikUVSmspEVVA%2Bn6eRwmKxGB%2BN1yujXC5HW2jsl0bJSedHjhxhg7GTk5MpJthVX8dG47r07np1nmESUtY0bb5IiSDYzw8lH3hT4q3%2B8ubbTiMHohHj6z8ILym628fCbpdNbOs1p%2BdWPnc6OzsHBgZoGLY%2BmdR8TlmWlU7PLWpRVZVGX3O5HC22i8Vi3d3dGGOMcW9vbywWq6%2FpY1UtveOCvMEr73rV5DkA2Kxol%2F%2Bx%2F2%2B%2FHv3eZycA4Ok%2F%2BYFbIjf85KyvO25qFgKAoGiS6vZlo4FQKEQeQJIkwzCy2WyxWGQj4EsSFbpIJEIiYoFA4ODBg0TqaTk11VPLU6%2FCub4K5KHs4QAAPNwdZ6ZI8gUALG7pdPrhqnjn%2FlVzQmkyiUgKmRqGYZBczDGBGBpElCSJpHscqZwV%2BQbpmgAVmMP9Lnu04GLsK1qy2ru3Zvx1JkNqPlzYvr%2BzQ18BjGDnhXR0QZZpmuyoNZQOeuEyTXOL7B01EOhwVXxYC%2FhN7BewoNl37u%2B44dJMRecA4LKzC0t2dEGpdFkhvzWX25rLXVbI1w9Zk9xKvb5gn9kwjYY9sBk5ej7taoWjRu%2FVuB%2BOQR537u%2B4d7ytTTTjVdeGbn3bVWlSsXDLlemfvOhtivbQdel5O7jb36BOmrqWbOidWDGaxBQFkdp4UtzJmjN6Wv1Eo%2Bcoy424OAA25bZUKtEcIGugFyAPAl8B4M0DOhE0AIi2GdduamYWb0wm2X8%2BpTaAKTQHnEwmc7mcpmm0TJcaOODmssgzMzNEMem6TrACZZ1qPYzxxMREuVxOp9NE8S3Du6CySd4BrV2WXTKFL%2Bl0ulwu0xJ2Wm7SAK899OuAIttk%2FWgmJ9x%2BTSqqNq7SvzGV2ppbMKb7PEpDmadQNpVKJRIJImgIITbr093dTX4cPHgwHo9TXimwJKCEuqtHjhyh6WR67WIzi%2BAsdmpTRZlOp%2BPx%2BIEDB%2BaKbjmgC5kI7qNIk9SaLBqVHJ1wXbM5XyzzAm%2B%2FOCHv%2FGWwt2ZcWCpNi6IhCB01a1Op8G%2BJqbMr8%2FEJC%2BCjA4OFRZCUx%2BPheZ5NdKuqyroKZGp4PJ5yuUyRpCzLvb29jthRIBBwLLfo6elhq0NIaYQoiqzXUavVarVaIBCgoQGe5zmOY0Ms7e3tRKm5XC6Xy8XOSp%2FP19%2Ffz4pz42zLXVdNk5jHGTetx4Af2n9EtcoWAA9gMZWRu%2F1qjhfeXir%2BWFVbiUo2T3SzT77kOU1y%2BA0PLXa%2BZVk84herrVuMk8aRojse61Q9%2BNC0iAG%2FrVgkq5TIPcnfcZf75v4eAJAk%2B39qba2r3lYUUCsedRPT7DhErNBi5zcvn1iMkyUye6Itfnf05fqOt65ff%2B1bM7dfkyIjT0TyjRMBX2oicMY3OjstRkAsgHGXGzC%2B%2FQOpRFpMpMVsnv%2FKhxOvlwemSy3YNRf17Yut12gpb4ABdqvqblXlbVvGWADOBFtHYlSd3%2BehXEGbzim%2F7uRlsZIZ0s4erV9F32p2w%2BI4bV4F4EReBARuBRc01N9h3LKj%2B9Seko4hbjUfWk8PPhlaH62Kor39%2B%2BEfveB7vTw%2F9T1abF%2BONVij5ViDNWosa2fH%2BqvgWhuINTreJJwsOeutGesrZb%2BFASApCqOyJyWuaYtTWtRO%2FC3PqFQ%2FnpzqMGqsm2YBvKwoX4tE1wTulDWgqwLWeBuJYPXJtW632SGZAd5SJezhsYRwDSPNQvka2ltUni8qvTXj9kSiy2i8mGlKlG4e6Nc5bu3FrGk1J4Vk65bo7DWeHACAAuACkMHkOVL4QcjtsgXNfnAi9HxRqXK8jgSAxqKmI2HtlZyqtBzHPaoam2IVWcAzRaFiohfz8lBHrT9gmCpXslEVc8bCegXD4ngFemXj6WnvlC2MyN71uu63DLTQgL6kKHdHoxo6mQa0VqvNzMxMTk4WCgWe54%2FJm3%2B9kG3bmqaReGHr9Qwn2oCGZOuGd2au25IFE6Y14db7u%2Bji7s8PJd%2FbVTA98%2FqMVhnN6zbL3v5SeMdkCBASLf48TeupaQDwiuLeJ7vgZJtNImdsFo1dDXpqUKVSSSaTNL0nimJPT8%2BJEbhj0GrXbsrt%2FNSRc4f0Q5OiVuG7wuZfvqV0cFLan5IA4KcZb83g3m6VXbY9jYVXc%2FIrs66XZ12Tmlg1kZu3%2FSaGNGxyl28enj3HX%2BkQqikXeiWoTCpSb8i4KlK468zpm%2FsyL%2BblI9WTs1TSsqxyucxmWRVFUU6tZSe6rheLRTbJ7vF4ToyotaTVZN6%2B76bERRvK2Txf0BDddCfabQCG7Y%2BF%2F%2BunQZK%2Fkm27xvGLZffakPWO9tKV3YWNUgUA2DCL6Tlafpiwt6fDD06GT3yKsF6rsbuInBpUKpVmZmZYrdbV1cUW0ZxMtyAkW%2Fd9NHHOOp1UZQkslMIACDQdiQKQihOd42BxEZnF%2FKPT6qPTqmzbNw%2FOXt%2BXARnmtuo5miB0R2GbklYlfO94W%2BuuaK1WI9Ursiw32ZwCY6zrumEYgiAoitI8t0%2BPWpal6zopN%2BI4ThRFSZKW3OqAsGTbNtktshWWZFleslvLsizLMgyDlj8hhCRJEgSh%2BbWkxoVWtJBqNgAoFoukfEsURZfLVT8mpmlWKhWMsSRJsiwvVjRh23a1Wq1Wq2RDznpNuYRW4217%2B3XJLRcWs3m%2BXJlnQhLs9rD5yB71rse6lq1%2BYq7qHWemNvoqhQXyO%2Bexfnak8%2FFksJWKYFJhRv%2FJ7t%2FhsB2pVIqt3O%2Fv72eFgNVq9E00ofb29mAg2BBitshSrVZLJpMsS%2Bw%2BIw6JzOVybJ8NKRgMhkKhepkjm4c7ZhGp%2BGEf0%2Bfztbe3s9VbpVKJbhhKZnJ3d3f90kBScM%2Fu2EtryJthtTZkIdM2EAIAm%2BMkZF%2B4oRLwWsXS3AO4FdwWtr79o%2BA93%2B%2BwV7AwZ9YSXsrKMbU2qBlVN8d6rK6KHQ2Y%2BwpSsia2YhTYt8XzfMMShFqtViwWHSPLTj4Wq5GaJ4ppiCbjOM6x%2FU42lxUEoV5pFYtFliVJkrweb71QEjXD6idFURr2RmpCW4Fi2WyW9MO2ezweolw5jrMsC2NMno7jOK%2FX6%2FV6PR5PMBgMBAIOMa1UKiyiME3T5%2FM1FDVN09i9n2RZdqjAuWtk2%2F5gNLvtrDTk5yHUNBa%2BsK%2F9ief8Tzznv%2B2Kmeu2ZAlWC6rWsy%2B6d%2F5iFVyzeNX1nYnARrXiL2FgV%2BPOwDBUz%2FdV%2FlSQreXW2a6EiEjJshwOhx0LLovFYjqdJhKJMU6lUgghdm1WA0TMccv2rzVNcygzWZbb29sVWSF9GoYxOzvLFjvNzMwghByLdDwej8fjKZVK5FshdFoGg8HWsRpCqKEBbaUUUSBq7ItnJTeDBgAFz%2Fx7anNZX4tOneWrfvlg%2BItPtEdC5pYLi0HVAoAX9surtaXOT2bVc9JeADD2g81xAMDZtgjg4bFmIfvkZQ5IPW%2F9wl6fz8dxXDKZpFtlF4vF5qK2wvAE6xR7PJ5IJMLqHlEUI5GIIAjsBmGlUkn1q%2FXyTfU0LerGJ2qzWQQAQ97qsL8KCtDNNOcMRJWDAPxZpyZjAQAOTR8XlxgD5jF2YVu0Rd4WeVsUAXiMTYMDe5XvuCTodpy8GJxXFIVd5KXresNP%2FiwnIrBwatm27RCFxTwSURRZdW5ZFl0OVG%2FsTsrUFQDgNwX3dw4EtvWm%2FRomO0pSbA4An9%2FXriMzqhoXnVkGgERSjEaMc07XyfdSVs7B24rFT9Wt%2BiT0v%2BH2%2FwsGYCnF1vpKFnaUV2Jnl6xedxzFGLe4H2397notap36zldFXS17DwKEEM8t8OnmHmzHZGjT3tO3Hw5P5ufQ2x%2BT8mdHOoefif2m4N7Qre%2B4eS7eYWLI5vmLNpTftymPVlwk2Fsz3lEoAAC%2F8D8ASInSK4q7FaDmQKmGYTScuKZpsu08zzsu5HmeVRiWZTX8FkS9GpMkyaH%2FHK4%2BG5twtLNQup6lk06CILDSjzFe7PsYjnXwPM%2FjxeJqs5jfMRnaMRlaaF%2FRVz6c2HJhsaJzNK5Goh43%2FlXGJdpfeqJz2cGO3ppx03RyQ6VSbw94gB8EA%2FvkllKQLpdLlmX67nVdTyaTHR0d7PsuFAqzs7PsRHe73Y4IHM%2FzsixTfE1WjLtcLofBqtVq2WyWFTWv1%2BuY%2FfUspVIpB0vFYtHBkqIoJ2C7eJ7nWbeg%2BcmSJHk8HnYR2dTUVCQSYbFpfRRJFMX6LMvS2YKQbO38xOF10RoRNZaiESOv8%2FfsbH%2FqBd%2BxbQmA0IemZ%2BhmxE4zB%2FBkILCzrU1rGVoVCoXkwqWprDGqNyVk%2BV9D6zAzM0MXmbIDR1fwOqbvYhmFUqlEXYcWWaoPWREPl%2FUug8Fge6OdswqFQiqVYtc3dnZ21mNNsorWIRZer5dsA16tVt1ut6qq7JTQdX1qaqp%2B8w4anKtnpmF0cGl1ndH5D%2Fx7L0kYTM8IusHNB1wRqLIVCZiGyUMLsVYZC2%2FRsu8oFC5otJc8lbPvBdv%2BOxw6JpTg9%2FsVRclms2ygsuEoiKIYDodZUF8fmPV4POz7MAyj4de%2BfD5fW1vbYnrI6%2FUODAxks1lWcBuyhBDq7OxsyBIb22sOnhwxP8uyGoJRt9vt9%2FtZUSPKmxUsSZJYUZNleWBgIJ%2FPpxbukdzwWdrb2wOBQOOASIuVHQjQ9Zemt12VBoBDk6KAIBoxNB195lsRunvAezNZslHAiKxMSFKOFwBAsa0Ow2g37cFq2SFSfJ2Q8QB3dw%2F81rsiI6Lreq1WI8iMxCoRQoIgiKLYSuaHheSVSoV0Rdb%2BchxH8JwkSceUhicZm%2BWxRKKjmqYhhHw%2BX5Nd1Ugq3TRNRVGaJ9GJeiaPRvkhSNHtdjfhh2g%2B0zTJhWQ9tCAIJKvWPG1%2FbEVEUdW44Z2ZqzfnARYWESF0YzLp2CdgMaWVEqUfq%2BrzbvWwy2XwFgDIJlqnl1TL%2BJXXB2sVuKcoLafgO6oaF2%2FQ%2FnhQJp%2BGUC386clEQ3TvoDzv%2FkJXmHzt4C2DlSs2Fs7oqwLAvgnXr1%2F17H7R%2F4Za8L1adDy2z3%2BtiBpLHQb%2B9FRinb60nBV58WN9%2FSkRXbJB2379lEfAMzmhZnIAIPB2Z7sJALf8Z%2FcSm%2FmsUZ2csYB1yXZgvjlADy32sYIm50Ojte70pg1Ff6VRnJSItvX1AgBv292G2VfVI4bZU6uplilj7LKhyoGOUEoUX1SUlEsIScaHLsl6ZDw9I5hHnVbT4hJJMdpt%2FMu1qb13KhmdX5Oh1v2heq3WXHSaSEPzG9GuWhHQ1Re1eRDGcYcl8bDUNH%2BAcb6CciUeAPw%2BK5URiDNrYpBFGzAcOCKVjbXFea9XoW8ucyc6Nm1x3G07I69MuLb9TbpfMFhG2GreNVq5qmtdgbHnLxv2LdnDydy0IyRbXSEDAKYy4prRPOXpZGbcMjqfmVyTsDcKrQGjNTpB9P93xGZwBc9tSgAAAABJRU5ErkJggg%3D%3D

```

---

### Post by tjwoosta on 2009-04-03
also if anybodys interested i just made a new dark ubuntu about:blank page

[http://userstyles.org/styles/16638]("http://userstyles.org/styles/16638")

---

### Post by TheSlipstream on 2009-04-04
Hey, good work. I've always hated going from a dark YouTube (or whatever) to a super-bright UF. Do you think you can fix the reply box? It's still white. Also, most images haven't been changed. Just in case you make this a big project. You could also make announcements appear gray, because that green announcement is driving me crazy. Another thing is, links are some kind of yellow green. Ugly. Gray is better. Anyway, really nice work.

---

### Post by tjwoosta on 2009-04-04
> 
Do you think you can fix the reply box? It's still white. Also, most images haven't been changed. Just in case you make this a big project. You could also make announcements appear gray, because that green announcement is driving me crazy.


i wish i knew how, read the previous pages and you will see that i too want theese things changed

im still struggling to learn this stuff myself

all i did was find an existing userscript, and modify it to the best of my ability

if you or anyone else knows how to change theese things please feel free to help

> 
Another thing is, links are some kind of yellow green. Ugly. Gray is better. Anyway, really nice work. 



yea i tried to make the links ubuntu brown/tan color

feel free to change it 

(right click on the stylish icon in the bottom right and choose manage styles, then choose ubuntu forums dark and click edit)

see where it says 
```

/**TEXT**/
* {color:#8A8A8A !important;}
.smallfont span, *:link {color:#796646 !important;}

```

change it to whatever colors you want

---

### Post by tjwoosta on 2009-04-04
YES!!

i finally figured it out

i just did a major update guys

i fixed all of the announcement box and reminder box and thread label boxes colors  as well as some minor changes to link colors



TO UPDATE: 

right click on the stylish icon and choose manage styles, then click find updates

---

