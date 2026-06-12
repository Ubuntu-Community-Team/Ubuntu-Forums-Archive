---
title: "Apache PDF Issue"
date: 2014-02-24
forum: Server Platforms
---

### Post by bianchirick on 2014-02-24
I am running server version: Apache/2.2.22 (Ubuntu) and I have an  issue where PDFs will not open in the browser properly (all non-IE  browsers), I just get gibberish (see below). ls there a setting in  apache that I need to set?


Example:
/my-server/svn/DocChecklist.pdf

%PDF-1.5
%Çì ¢
5 0 obj
<</Length 6 0 R/Filter /FlateDecode>>
stream
xœí][  Å  ¶‰íÅ2  À\Â! pLØaúÞM’—(y‰ò’hß O$ !‘ çÿKéËÌtUuõ9söÌ: À š*í{W}õuõe¿Û ƒ »1ý›?¾üöâÓ¿»Ý×ÿ½ønç„Ë2)ìÎ„°³£÷% ßýé?  »È9wO¿¾øîÂ *ý— ðûËow ¼Š9B”ŽzwõÕÅ8„àGgò¯ÅÎÉTµÓf rwõíÅçû ž\Ææ a "ßÿ¸úK,Jˆ  ¨0ï¦Â¤2ƒ"¥Ýº Ê Â Rìï¼˜  Áj»ÿ øÅÝ{OÆa4J8ã÷÷Ó÷è‚ G³ÿâß9™R!¶áÖK¥AA a Ëz&#65533;Ê‚EÁï/ž> ±ÁZÙýÝ‡Q {eF k{ùIªËZ%÷¯ÀöÝNY*“zÿ¨æ|  ^ xíÞ éÕ G]†¬;úÊ¹ô 2üR 5˜°fÄ $ó »sõMÊ£jžKmÆÁ[µ» r vwõÏ‹XvLfƒÊ?ÿõâêãÏ÷·RÏ¤6ìoßIã ÆQë8ÌQ¬GiDœ±Ez7 ¾SÚ[˜â^-£èŽ—.ÈØ¨8|ÎŽbšN¡FéÅþ¥ ²|ô*¦¨â 5õS˜qþŒ% eS—§!Ò*É~bÇ>ß?Œ¿ = ~n£Ñ~ÿòí©ª`—B¥Ÿ²ÿùj6¦ÁŒ" •lÊ˜dqNîT0Ñ¦vOÿuñÕÇ§˜œ0» Gw™u9Mš 3 [ ç	O  Þë2 ±œ¨B·Ó§wB«ý üé*p1Á¥ÔQ[c/^Œê §S˜y.¬5B•	PÒF ½ ó-Ò4 q|¼—!Y W*Ž•Þ ÃŠÖ  Lý   ´= [N2š8´ kó@ )Ij“—Ù bJãt(†>ú¨ Áï_©%>ªŸ¯Â$½ô¯Á¬± a´zÿóå+
ˆ±Æ ~ÿ‹\‚ñAK Çoê°ß¿ž X§¡‚ Dõ½‘S å£ÒäÞDó×û7kêÇì°¢2¦	qÁ»Î„Üƒ9e4w-|RE•ìy »Ô #‹B¿QÓ  Ý·²ÔX·  Ï\ž–pKŸ°&¤Ú#LDDÊh3W » Š ãñp*%*í; 1µ‹¶“Tu ÇwkS›!0Æz( ÊþvnjDc K -Í&kŒNŽÑìtü—ì“•ø"±ZÌ²¤å$™ £*" »:KÕ § 'Œ"SDNÛEèL“. Â”Î/Bm *˜ åNøØ ½  ÔA“‰°4 
s[ˆ°ÔB„ç@˜ Ý`õÎúhm¾àØ/« &#65533;t¸_ ï½*}» +Q%Ëô  ‚Ó &#65533; P  „ï×²‘%þ

[FONT=arial]Thanks in Advance,
Rick[/FONT]

---

### Post by SeijiSensei on 2014-02-24
You shouldn't need to change anything in Apache to distribute PDFs.  How a PDF is displayed is determined by the browser.  In Firefox, take a look in Edit > Preferences > Applications and see what application is associated with "Portable Document Format".  I use Kubuntu, so for me it's set to use KDE's default PDF viewer, okular.  On Windows machines, it's usually Adobe Reader which plays this role.

---

### Post by koenn on 2014-02-25
> **SeijiSensei said:**
> How a PDF is displayed is determined by the browser.
doesn't the browser depend on the webserver for a hint about what sort of document it is serving ?  MIME type  or so ?

---

### Post by SeijiSensei on 2014-02-25
Yes, I guess my post was somewhat misleading.  By default, Apache uses the standard /etc/mime.types file which includes the mapping of the .pdf extension to the "application/pdf" mimetype. Apache will then send a Content-Type header during HTTP negotiation telling the browser the mimetype of the associated object.

bianchirick, make sure you have an /etc/mime.types file.  If that file has somehow gone missing, you can recreate it with the contents of [http://svn.apache.org/viewvc/httpd/httpd/trunk/docs/conf/mime.types?view=markup](http://svn.apache.org/viewvc/httpd/httpd/trunk/docs/conf/mime.types?view=markup).

However the browser can also make use of its own or the operating system's mime.types file to map from extensions to mime types.  I'm pretty sure that even if the server used a generic mimetype like "application/octet-stream" the browser would still select a PDF reader if the file has a .pdf extension.

From bianchirick's description of the problem, where IE works and non-IE browsers do not, it sounds more likely that only his IE browsers are configured to launch a PDF reader.

---

