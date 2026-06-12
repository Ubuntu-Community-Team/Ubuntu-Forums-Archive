---
title: "Trouble with conky weather."
date: 2009-06-09
forum: The Cafe
---

### Post by sm1g on 2009-06-09
As the threads title states, i have trouble with my conky weather script.
A few days ago i formated my drive and re-installed Ubuntu. Tho i thought i had everything backed up, i forgot the weather script. Now, when i tried getting it back, i am expieriancing major difficulties. Basicly it was a nice weather script and showed me the current temperatures outside, the "Feels like" temperature, a forecast for tomorrow and wind speed.

I got my hands on a few other weather scripts but they all seem to have the same problem. It's not parsing the weather.xsit file and gives out this error report:

```
sm1g@homebox:~$ conky
Conky: desktop window (3f) is root window
Conky: window type - desktop
Conky: drawing to created window (0x2000001)
Conky: drawing to double buffer
-:1: parser error : Document is empty

^
-:1: parser error : Start tag expected, '<' not found

^
I/O error : Invalid seek
unable to parse -

```

As you can see, it's not parsing the damn file and says it's empty. It is not. Here are the files contents:

```

<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0" > 
	<xsl:output method="text" disable-output-escaping="yes"/>
	<xsl:template match="weather">
		<xsl:apply-templates select="cc"/>
		<xsl:apply-templates select="dayf/day[@d='1']"/>
	</xsl:template>
 
	
	<xsl:template match="cc">
		<xsl:text>Location: </xsl:text><xsl:value-of select="obst"/>  
<xsl:text>:
</xsl:text>
<xsl:text>  Temperature: </xsl:text><xsl:value-of select="tmp"/><xsl:value-of select="/weather/head/ut"/>
<xsl:if test="tmp != flik">
<xsl:text>
  Feels Like: </xsl:text><xsl:value-of select="flik"/><xsl:value-of select="/weather/head/ut"/>
</xsl:if>
<xsl:text>
  Conditions: </xsl:text><xsl:value-of select="t"/>
<xsl:text>
  Wind: </xsl:text>
<xsl:choose>
	<xsl:when test="wind/s = 'calm'"><xsl:text>0</xsl:text></xsl:when>
	<xsl:otherwise><xsl:value-of select="wind/s"/></xsl:otherwise>
</xsl:choose>
<xsl:value-of select="/weather/head/us"/> 
<xsl:choose>
	<xsl:when test="wind/s = 'calm'"><xsl:text>(0mph)</xsl:text></xsl:when>
	<xsl:otherwise><xsl:text> (</xsl:text><xsl:value-of select="round(wind/s * 0.6214)"/><xsl:text>mph)</xsl:text></xsl:otherwise>
</xsl:choose>
<xsl:text> (</xsl:text><xsl:value-of select="wind/t"/>
<xsl:text>)</xsl:text>
	</xsl:template>

	<xsl:template match="dayf/day[@d='1']">
<xsl:text>
  Tomorrow: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text>, </xsl:text><xsl:value-of select="part[@p='d']/t"/>
<xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/>
<xsl:text>
</xsl:text>
	</xsl:template>
</xsl:stylesheet>

```

If anyone knows where the problem is, i'll be happy to recieve help. Currently, im frustrated with this thing.


[COLOR="Red"]**UPDATE!**[/COLOR]

Nevermind, i just realised i didn't have CURL installed.
You can delete the thread or leave it for future reference in case someone else forgets aswell. :)

---

