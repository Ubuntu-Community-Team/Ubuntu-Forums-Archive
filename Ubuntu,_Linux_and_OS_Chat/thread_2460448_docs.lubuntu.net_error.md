---
title: "docs.lubuntu.net error"
date: 2021-04-10
forum: Ubuntu, Linux and OS Chat
---

### Post by goeft on 2021-04-10
Hello, 

I would just like to inform whoever is responsible for it that when I go to [https://docs.lubuntu.net/](https://docs.lubuntu.net/), as linked from [https://lubuntu.net/](https://lubuntu.net/), the following error appears:
[URL="https://ubuntuforums.org/attachment.php?attachmentid=288255&d=1618055563"]
[/URL][ATTACH=CONFIG]288255[/ATTACH]

Left frame text:

> Whoops\Exception\ErrorException thrown with message "Trying to access array offset on value of type null"

Stacktrace:
#14 Whoops\Exception\ErrorException in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:1229
#13 Whoops\Run:handleError in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:1229
#12 Grav\Common\Page\Pages:buildSort in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:298
#11 Grav\Common\Page\Pages:sort in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:1112
#10 Grav\Common\Page\Pages:recurse in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:1077
#9 Grav\Common\Page\Pages:recurse in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:948
#8 Grav\Common\Page\Pages:resetPages in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:928
#7 Grav\Common\Page\Pages:buildPages in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:213
#6 Grav\Common\Page\Pages:init in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Processors/PagesProcessor.php:24
#5 Grav\Common\Processors\PagesProcessor:razz:rocess in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Grav.php:132
#4 Grav\Common\Grav:Grav\Common\{closure} in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Grav.php:379
#3 Grav\Common\Grav:Grav\Common\{closure} in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Grav.php:355
#2 call_user_func_array in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Grav.php:355
#1 Grav\Common\Grav:__call in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Grav.php:133
#0 Grav\Common\Grav:razz:rocess in /home/lubuntun1/public_html/docs/index.php:52



for some reason, including the text of the right frame creates a "forbidden" error when I try to preview the post. maybe the forum thinks I am trying to pass malicious code. so I will post this and try responding to myself with the remainder.

---

### Post by goeft on 2021-04-10
sorry I am not able to post the text of the right side frame because the ubuntu forum throws an error. 

I put it here: [https://rentry.org/vmkk4](https://rentry.org/vmkk4)

have fun :)

---

### Post by CelticWarrior on 2021-04-10
Welcome.

Lubuntu.net isn't the official Lubuntu website, [Lubuntu.me]("https://lubuntu.me/") is.
Please always check at [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) to avoid being duped.

---

### Post by GhX6GZMB on 2021-04-10
Yep, the .net site is a cybersquatter. Avoid referencing it, it just brings it more traffic.

---

