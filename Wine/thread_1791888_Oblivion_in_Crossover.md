---
title: "Oblivion in Crossover"
date: 2011-06-27
forum: Wine
---

### Post by texasboy2084 on 2011-06-27
I installed Oblivion in crossover games, it appears everything install correctly (since the launcher, and everything in it works fine.). But when I click start it opens notepad and gives me this:

```
<html>
<head>
<title>Activating product...</title>
<meta name="am-version" content="5.42">
<script language="JavaScript" src="am_include.js" type="text/javascript"></script>
<script language="JavaScript" src="author.js" type="text/javascript"></script>

</head>
<body topmargin="0" marginheight="0" leftmargin="0" marginwidth="0" bgcolor="#FFFFFF" >
    <form action="#" method="post" name="buyform">
        <script language="JavaScript" type="text/javascript">
            AM_Init_Purchase(document.buyform, "connect.html", "connecting.html");
        </script>
    </form>
    <script language="JavaScript">document.buyform.submit();</script>
</body>
</html>

```


I bought it from direct2drive sometime ago if that matters.

gpu is a ATI HD 5770 (all drivers up to date)
cpu AMD Phenom 2 x4 3.4ghz
OS Ubuntu 11.04


Any help would be greatly appreciated :)

---

### Post by handy on 2011-06-27
Codeweavers offer great support on their forums. The dev's often get involved when necessary & obviously watch the forum quite closely.

I would think that you will very likely get an answer if you post in the appropriate section of their forums over there.

Not that I'm trying to fob you off here. I'm just passing on what I know from experience. :)

---

### Post by stevedude on 2011-06-28
Just a comment. I too have Crossover games installed and I noticed it caused a file association change with my files. For me, it was mp3 files. They are now associated with Crossover, and when I clcik on an mp3 file, it opens the Crossover installer.

I had to "right-click" on an mp3 file and choose "Open with" and then the program I want it to open with. I would do the same with your Oblivion executable because its obviously associated with notepad.

---

### Post by handy on 2011-06-28
The Crossover (Wine) dev's need to hear about these things so they can get to work & fix them.

---

### Post by texasboy2084 on 2011-07-19
Totally forgot about this thread. I solved it by install IE8, turns out the DRM that is used in the Direct2Drive version needs stuff thats in IE8.

---

### Post by handy on 2011-07-21
> **texasboy2084 said:**
> Totally forgot about this thread. I solved it by install IE8, turns out the DRM that is used in the Direct2Drive version needs stuff thats in IE8.

Did you post this on the Crossover Games Oblivion forum?

If the info' doesn't already exist there then it could save lot of people a LOT of time.

---

