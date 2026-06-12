---
title: "Possible problem with ja_JP.UTF8 code page"
date: 2009-07-05
forum: Wine
---

### Post by leunvcy on 2009-07-05
As I am not too sure about the rules, I will describe the program I am trying to run with Wine 1.1.25, instead of saying the program out loud. The program I am trying to use is an P2P program, which has been "temporary" closed down by RIAA on 2005. I suppose this describe is somehow clear enough. ;)

While I can start it with no problem in Japanese with locale set to LC_ALL="ja_JP.utf8"&#65292; I have no way to type Japanese directly into it.  When I try copy and paste method, it displays the letter/character in the field but the resulting tab shown squares instead of the same letter/character. Even if I somehow got some search results by searching in English, when I tried to download anything have accent/strange letters. I receives "wineserver: file_set_error() can't map error: Invalid or incomplete multibyte or wide character" in the terminal. It won't start the download and tells me "File Error > (1) "An unknown error occurred while accessing [File Name]""

But when I tried it with LC_ALL="zh_TW.utf8", it can display Chinese, download Chinese files.

I have been searched all over the net but no luck. Tried Winelocale but still the same.

Any help is much appreciated.

P.S. I am new to Linux. Please treat me tenderly. :p


# Further Information #

When I 

$ locale -a

...
ja_JP
ja_JP.eucjp
ja_JP.utf8
...

However when I tried

$ locale
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
LANG=ja_JP.UTF-8
LC_CTYPE="ja_JP.UTF-8"
LC_NUMERIC="ja_JP.UTF-8"
LC_TIME="ja_JP.UTF-8"
LC_COLLATE="ja_JP.UTF-8"
LC_MONETARY="ja_JP.UTF-8"
LC_MESSAGES="ja_JP.UTF-8"
LC_PAPER="ja_JP.UTF-8"
LC_NAME="ja_JP.UTF-8"
LC_ADDRESS="ja_JP.UTF-8"
LC_TELEPHONE="ja_JP.UTF-8"
LC_MEASUREMENT="ja_JP.UTF-8"
LC_IDENTIFICATION="ja_JP.UTF-8"
LC_ALL=ja_JP.UTF-8

When I set it to "zh_TW.utf-8

$ locale
LANG=zh_TW.utf-8
LC_CTYPE="zh_TW.utf-8"
LC_NUMERIC="zh_TW.utf-8"
LC_TIME="zh_TW.utf-8"
LC_COLLATE="zh_TW.utf-8"
LC_MONETARY="zh_TW.utf-8"
LC_MESSAGES="zh_TW.utf-8"
LC_PAPER="zh_TW.utf-8"
LC_NAME="zh_TW.utf-8"
LC_ADDRESS="zh_TW.utf-8"
LC_TELEPHONE="zh_TW.utf-8"
LC_MEASUREMENT="zh_TW.utf-8"
LC_IDENTIFICATION="zh_TW.utf-8"
LC_ALL=zh_TW.utf-8

---

