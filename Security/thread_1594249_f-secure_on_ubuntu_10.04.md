---
title: "f-secure on ubuntu 10.04"
date: 2010-10-12
forum: Security
---

### Post by eewoud on 2010-10-12
I'm trying to install f-secure on ubuntu server 10.04. According to f-secure their product is supported for linux server 10.04. Unfortunately when I try to install it I get an error message. When I go to the log it says "please use alien to install rpm packages on Debian, if you are really sure use --force-debian switch."
The problem is that there is no rpm to convert with alien since a script is used for the installation.
 
this website: [http://forum.f-secure.com/topic.asp?TOPIC_ID=11203](http://forum.f-secure.com/topic.asp?TOPIC_ID=11203) describes the problem, but no solution is found...
here is the google cache, in case the website is down (as it appears to be now): 
[http://webcache.googleusercontent.com/search?q=cache:hL5zGPtc44oJ:forum.f-secure.com/topic.asp%3FTOPIC_ID%3D11203+rpm+f-secure&cd=2&hl=nl&ct=clnk&gl=be](http://webcache.googleusercontent.com/search?q=cache:hL5zGPtc44oJ:forum.f-secure.com/topic.asp%3FTOPIC_ID%3D11203+rpm+f-secure&cd=2&hl=nl&ct=clnk&gl=be)
 
Does anyone know how I can get F-secure antivirus for linux server working on ubuntu server 10.04?

---

### Post by OpSecShellshock on 2010-10-12
You'd probably need to open the shell script in a text editor rather than just running it, in order to see what steps it's going through. It appears that the installer is intended for use with Red Hat. If it's possible to just view the text, you can go through the commands individually and find the point at which a package installer is being used, and put in the alien command prior to that point.

---

### Post by eewoud on 2010-10-12
I only get a few number of readable lines when I open it in a text editor. I can't find any package installer in these lines. The rest of the file contains unreadable symbols.

here is part of the code:
> df#!/bin/sh
skip=40
unpackdir="/tmp/df-setup-$$"
cleanup() {
 cd / ; rm -fr "$unpackdir"
}
sigclean() {
 die 10 "Terminated by a signal. Cleaning up temporary files."
}
die() {
 cat  >/dev/stderr <<EOF
$2
EOF

cleanup ; exit $1
}
if [ "$1" = "extract" ] ; then
 oname="$0-$$.pkg"
 cat <<EOF
Extracted package compressed with gzip and packed with tar into $oname.
EOF
 tail -n +$skip "$0" | cat > "$0-$$.pkg" ; exit 0
fi
if [ "$1" = "rpm" ] ; then
 echo "Unpacking self-extracting package $0 into currect directory..."
 tail -n +$skip "$0" | cat | gzip -dc | tar -v -x -f - 
 exit 0
fi
rm -fr "$unpackdir"
trap sigclean 1 2
mkdir "$unpackdir" || die 1 "Failed to create unpack directory $unpackdir.";
if tail -n +$skip $0 | (cd "$unpackdir" && cat | gzip -dc | tar -v -x -f - >/dev/null) ; then
    cd "$unpackdir" || die 2 "Failed to chdir into $unpackdir"
    /bin/sh ./product-setup "$@" || die 5 "Failed to run setup script."
    rm -f "$packname"
    cleanup; exit 0
fi

die 2 "Failed to uncompress package in $unpackdir."
&#8249; &#8217;þSL ä<isÛF²ùJü&#352;1ÌDÇ@R&#8225;eK¡w&#8240;êÉWGâ<Ë¡ rHbEÄØþï¯»çÀI&#8240;v*©ÚZ¥"3====}ÏÀÓ(ì'½Ø<N¦ßü5?Møyñbþ®omnldþÂO«¹µÝj~Ójm®onoo¯·*½µõb£õ
kþEôä~{cß&#8222;w7nÜ¯&#8218;{ªÿ?ôçù³Æ4ÄÈ²&#382;3\£&#8221;6#vä&#339;ó^qvâÉ£?&#382;à~8Eþp³åÞ
k½zõÊYo6_¦#öÃhF^ì&#8225;ËöÆcv&#8224;Ð&#8218;qÁ£;Þwqº£0êqÆ£æ&#353;p!¼!,Ùa0û@ÑÉÞÛÛûÖÉ~wïäøà&#338;63ÙhY½&#8249;&#376;Úuü½&#402;Ùi$"&#8217;Â¼â&#8220;&#338;8wàM8,q6&#8226;:Àîùî ã±*ÎÙéÁåþEÛ&#382;Ã	ÛÚ?íüzvüãO óçyb[V/&#339;L¼*ß&#8230;éy7Æ³öÀnMü!&#338;äÝANº¸M&#8250;ªC-«4Îò&#402;&#732;G^/öïx;&#381;&#381;&#8249;Æ&#8482;b&#8211;L<qkÑoª¸&#381;=ÓàÙ0â<Æ&#8230;óÞ(dv]*_³&#8222;H·u§Yºnòß³k¿Ï&#339;ä&#353;9gMö}÷ûhÕ$À¯aÂ&*oì&#8224;³(cÜk&#8230;&#353;é¹löú»uðàÇ¬e}¶¬Ð$¦^/¯X-¦~4ÅaÓzw&#382;?önÆ&#339;,j&#381;øï	1ï3Pò!ÍxùÚ®·L&#8216;xÝ0§Ã&#339;[V&#8212;ì&#8364;úcXkÁ³wË&#8211;>Ê©ë&#8250;&#376;&#8212;®&#8216;B&#8222;ÉpÔ*"¶eêEY:$y°ðÅP&#8224;&#402;ý&#710;÷ÛuØ*ÝHÃÛõeÃMñ&#352;ñì=« s&#8224;@°FÄ>ì"w&#8482;Î'QÀ&#353;)SPÄæ@¥|d`ïÆ&#8220;i»ÕlæÀ&#376;³s¢ïÍ,à¼Óûk $Ù&#732;¬h
÷Ú[&#8230;«Q d5&#352;;/Z
&#8364;¬FNãöúB( ²&#338;"ãnV,ÚMËzÆ²-&#8217;õååºâÛj«¹¾¹²"&'&#8221;©Þ&#338;¼;õxÌ=!·"=e*R¡ä°m&#8226;"Ý*&#8217;&#8222;Õ$Áó×&#8216;&#8222;Hæ]_Jî&	&#382;¿&#381;$D2&#8225;$èúR&#8217;pÇ5Iðüu$!&#8217;9$A×S$^;&#732;ÃEWYOK&#338;Â{&#339;	DRËÔóböý÷&#8225;§GV¥}g
~Ç²./&#381;y %=&#8230;Ø&#8216;VÈq¼ìØÕ&#8226;U{szpÈÞÄt"ÚGç7ç&#8212;g'ÌëOüà&#8211;ÏÚ
ô¹&#8249;ÓÆÞÁ&#8250;ã·nçò&#8225;4jìÃ6>õù§{Ôò>?D|Æü>ñ¾ÃLAÓð&#8217;íËóÃ3½åQÀÇw<ò³OA&#732;}eSO&#710;vgïü¼óÓÙÞù¡&#8218;&#376;õÂ>oÿïá¯û@*eý2â`&#732;&#8240;r_0&#8211;ô½qp&#8250;Ô9}/p'²lð´ªô%`qÝ3¦&#353;óð&#8240; jb «&#381;ýÞ&#338;½!Ð¢*ãAJ&#402;Æ»ÆfZp 4¹óû&#339;!CÙ&&#8211;x,&#8230; "$&#8220;ÛC®Ije&#8364;C[á*3

---

