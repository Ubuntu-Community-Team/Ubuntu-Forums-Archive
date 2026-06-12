---
title: "Conky - El tiempo en español"
date: 2008-05-27
forum: Software
---

### Post by Bruce M. on 2008-05-27
Conky - El tiempo en español para Buenos Aires (ARBA0009)

[CENTER][[IMG]http://img138.imageshack.us/img138/7382/3conkysij1.th.jpg[/IMG]](http://img138.imageshack.us/my.php?image=3conkysij1.jpg)[/CENTER]

Usted puede verlo [aquí - #216]("http://ubuntuforums.org/showpost.php?p=5053708&postcount=216")

Localización - para cambiar el código de localización para su ciudad el URL siguiente se debe utilizar, substituye NORWICH por su ciudad:

[http://xoap.weather.com/search/search?where=NORWICH](http://xoap.weather.com/search/search?where=NORWICH)

Cambie "ARBA0009" para el código que usted encuentra en el URL arriba en "conkyForecast.py".

La fuente de weather.ttf y de arrows.ttf [está aquí]("http://ubuntuforums.org/showthread.php?t=760527"). La fuente de moon.ttf [está aquí]("http://www.dafont.com/moon-phases.font")

La escritura del email [es aquí]("http://ubuntuforums.org/showpost.php?p=4962990&postcount=154") si usted la quiere.

Que usted tenga un buen día
Bruce

PD: Pardon mi español, yo están utilizando [Yahoo! Babelfish]("http://ca.babelfish.yahoo.com/translate_txt") a traducir de inglés-español.

**EDIT:**1 Nov, 08: Hay algo nuevo, [ver #26]("http://ubuntuforums.org/showpost.php?p=6080251&postcount=26")

---

### Post by Mauro22 on 2008-05-27
Muy bueno!  Gracias Bruce!


:popcorn:

---

### Post by andy_91 on 2008-05-27
muy buen conky la verdad un diez para ese Xubu

---

### Post by Bruce M. on 2008-05-27
> **Mauro22 said:**
> Muy bueno!  Gracias Bruce!


:popcorn:

de nada.  :)

> **andy_91 said:**
> muy buen conky la verdad un diez para ese Xubu

si, tengo Xubuntu tambien.  :)

---

### Post by lega on 2008-05-28
me encanta!pero me mareo tanto código, no supe por donde empezar :(, gracias de todos modos, muy lindo

---

### Post by Bruce M. on 2008-05-28
> **lega said:**
> me encanta!pero me mareo tanto código, no supe por donde empezar :(, gracias de todos modos, muy lindo

Esto tiene tres conkys que intentaré ayudarle. Hay ayuda aquí: [dos conkys]("http://ubuntuforums.org/showthread.php?t=694880&highlight=Dos+conkys") tambien, es un viejo método pero ayudará también.

**PASO 1**
Usted necesita dos programas mas que los 3 fuentes arriba: (Synaptic Package Manager)
1. conky; y
2. curl

y quizá un tercer programa: python, si usted no lo tiene.
En una consola:
```
sudo apt-get install python
```
**PASO 2** Crear un archivo de ~/.startconky
```
gksudo gedit ~/.startconky
```
Este es mi archivo ~/.startconky. Copia y pegalo en el archivo vacio que creates anteriormente con gedit. Luego guardalo.
```
#!/bin/bash
sleep 30 &
conky -c ~/Conky/conkymain &
#sleep 10 &
conky -c ~/Conky/conkyforecast &
#sleep 10 &
conky -c ~/Conky/conkyemail &
```
El comando "sleep" permite que se configure tu escritorio antes que conky corra.

**PASO 2a:** Iniciando y parando ambos conkys:

**PASO 2b:** Automaticamente al momento de inicio

Yo uso Hardy. Si vos no usas esta version el proceso puede ser diferente:

Abri Sistemas-> Preferencias -> Sessiones -> Nuev
Nombre: Conky
Comando: /home/tu_nombre_de_usuario_aca_/.startconky

**NOTA:** si ya tienes conky configurado para iniciar automaticamente, editalo para que refleje el cambio hecho arriba con los cambios necesarios.


**PASO 2c:** Manualmente

En una consola:

Iniciando ambos conkys
```
./.startconky
```
Parando ambos conkys:
```
killall conky
```

**PASO 3** Crear un archivo de ~/Conky/conkymain
```
gedit ~/Conky/conkymain
```
Este es mi archivo ~/Conky/conkymain. Copia y pegalo en el archivo vacio que creates anteriormente con gedit. Luego guardalo.

**OJO:** Si usted no tiene la fuente: Zekton, la cambia para otra que usted tiene.

```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
default_outline_color black
default_shade_color black
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 white
color6 white
color7 white
color8 white
color9 white
alignment top_right  # or top_left, bottom_left, bottom_right
gap_x 10
gap_y 35
text_buffer_size 128 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades yes  # shadecolor black

TEXT
${font Zekton:size=11}${color1}${alignc}*** ${color2}GMT$color ${tztime GMT %H:%M} ${color1}***$color$font
${font Zekton:size=11}${alignc}${color2}** ${color1}Canada ${color2}**$color$font
${color1}Winnipeg: $color${tztime Canada/Central %H:%M}${alignr 2}${color1}London${color1}: $color${tztime Canada/Eastern %H:%M}
${color0}${hr 1}$color
${alignc}${color1}--> ${color2}bruloo @ bruloo ${color1}<--$color
${font Zekton:size=20}${alignc}${time %H:%M}$font
${font Zekton:size=12}${color1}${alignc}${time %A, %d %b. %Y}$color$font
${color3}UpTime:${alignr 2}$uptime$color
${color0}${hr 1}$color
${voffset 5}${color2}CPU:${alignc}$color$running_processes ${color1} /$color $processes${alignr 2}${color2}${cpubar cpu0 14,80}$color
${color1}${voffset -16}${alignr 5}$cpu%$color
${voffset 2}${color1}Load Avg (${color3}Min${color1}):${alignr 2}${color3}1: $color${loadavg 1}   ${color3}5: $color${loadavg 2}   ${color3}15: $color${loadavg 3}
${voffset 5}${color2}RAM:$color $mem ${color2} /$color$memmax${alignr 2}${color2}${membar 14,80}$color
${color1}${voffset -16}${alignr 5}$memperc%$color
${voffset 2}${color1}Buffered: $color${buffers}${alignr 2}${color1}Cached:$color ${cached}
${voffset 5}${color2}SWAP: $color$swap ${color2}/ $color${swapmax}${alignr 2}${color2}${swapbar 14,80}$color
${color1}${voffset -16}${alignr 5}$swapperc%
${color0}${hr 1}$color
${voffset 5}${color2}HD Info${color1} -$color Free${color1} - Used - ${color2} Total
${voffset 5}${color1}Root: $color${fs_free_perc /}%${alignr 2}${fs_free /}${color2}/${color1}${fs_used /}$color/${color2}${fs_size /}$color
${color1}Home: $color${fs_free_perc /home/bruloo}%${alignr 2}${fs_free /home/bruloo}${color2}/${color1}${fs_used /home/bruloo}$color/${color2}${fs_size /home/bruloo}$color
${color1}BruLoo: $color${fs_free_perc /media/BruLoo} %${alignr 2}${fs_free /media/BruLoo}${color2}/${color1}${fs_used /media/BruLoo}$color/${color2}${fs_size /media/BruLoo}$color
${color1}40G: $color${fs_free_perc /media/sdb1}%${alignr 2}${fs_free /media/sdb1}${color2}/${color1}${fs_used /media/sdb1}$color/${color2}${fs_size /media/sdb1}$color
${color1}W2K: $color${fs_free_perc /media/sda1}%${alignr 2}${fs_free /media/sda1}${color2}/${color1}${fs_used /media/sda1}$color/${color2}${fs_size /media/sda1}$color
${color0}${hr 1}$color
${color1}Desde:$color Buenos Aires, Argentina
${color1}Lat: ${color2}34°35'S          ${color1}Long: ${color2}58°21'W            ${color1}Alt: ${color2}25 m$color
${voffset 5}${color2}${font Zekton:size=12}hoy:$font ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=CC}$color${alignr 2}${color1}ST: ${color2}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=LT}
${color3}${font Weather:size=50}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=WF}$font$color
${alignr 50}${voffset -55}${font Zekton:size=25}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=HT}$font
${alignc 20}${voffset -30}${font Arrows:size=20}${color4}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=BF}$color$font
${alignc 10}${voffset 5}${color4}Viento: ${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=WS}$color
${color1}Humedad: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=HM}${alignr 2}${color1}Precipitación: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=PC}$color
${alignc}${color1}Presión: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=BR} - ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=BD}$color
${color4}${hr}$color
${color1}Salida del Sol: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=SR}${alignr 2}${color1}Ocaso: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=SS}$color
${voffset 15}${color1}Luna:${color4}${alignr 2}${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=MP}$color
${voffset -20}${offset 80}${color4}${font moon phases:size=20}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=MF}$font$color
${color0}${hr}$color
${voffset 5}${color2}IP:${alignc}$color${addr eth0}
${color1}Down: $color${downspeed eth0}k/s ${alignr 2}${color1}Up: $color${upspeed eth0}k/s
${color1}Total: $color${totaldown eth0} ${alignr 2}${color1}Total: $color${totalup eth0} 
${color1}Inbound: $color${tcp_portmon 1 32767 count}          ${color1}Outbound: $color${tcp_portmon 32768 61000 count}${alignr 2}${color1}Total: $color${tcp_portmon 1 65535 count} 
${voffset 5}${color2}Connections: $color${tcp_portmon 32768 61000 count} ${alignr 2} ${color2}Service/Port $color
${voffset 5}${tcp_portmon 32768 61000 rhost 0} ${alignr 2} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr 2} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr 2} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr 2} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr 2} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr 2} ${tcp_portmon 32768 61000 rservice 5}$color
```
**PASO 4** Crear un archivo de ~/Conky/conkyforecast
```
gedit ~/Conky/conkyforecast
```
Este es mi archivo ~/Conky/conkyforecast. Copia y pegalo en el archivo vacio que creates anteriormente con gedit. Luego guardalo.
```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
default_outline_color black
default_shade_color black
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 white
color6 white
color7 white
color8 white
color9 white
alignment bottom_left  # or top_left, bottom_left, bottom_right
gap_x 10
gap_y 35
text_buffer_size 1024 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades yes  # shadecolor black

TEXT
${color0}${hr}$color
${color4}${font zekton:size=9}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --template=/home/bruloo/Conky/scripts/myweather.template}$font$color
```
**PASO 5** Crear un archivo de ~/Conky/conkymail
```
gedit ~/Conky/conkymail
```
Este es mi archivo ~/Conky/conkymail. Copia y pegalo en el archivo vacio que creates anteriormente con gedit. Luego guardalo.
```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
default_outline_color black
default_shade_color black
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 white
color6 white
color7 white
color8 white
color9 white
alignment bottom_left  # or top_left, bottom_left, bottom_right
gap_x 565
gap_y 35
text_buffer_size 128 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades yes  # shadecolor black

TEXT
${color0}${hr}$color
${font Zekton:size=11}${color1}Tenemos  ${color3}${execi 60 python /home/?????/Conky/scripts/mail/conkyEmail.py --servertype=POP --servername=pop3.xxxxxx.com.ar --username=xxxxxx --password=xxxxxxxxxx}${color1}  email(s)$font
```
**OJO:** usted debe cambiar el código para --servertype=POP --servername= pop3.xxxxxx.com.ar --username=xxxxxx --password=xxxxxxxxxx a su información y ?????? para su "ubuntu login name"


**PASO 6** Crear un archivo de ~/Conky/scripts/conkyForecast.py
```
gedit ~/Conky/scripts/conkyForecast.py
```
Este es mi archivo ~/Conky/scripts/conkyForecast.py. Copia y pegalo en el archivo vacio que creates anteriormente con gedit. Luego guardalo.
**[COLOR="Blue"]EDITO: 06 June 08 - Archivo actualizado de ConkyForecsat.py[/COLOR]**
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
###############################################################################
# conkyForecast.py is a (not so) simple (anymore) python script to gather
# details of the current weather for use in conky.
#
#  Author: Kaivalagi
# Created: 13/04/2008
# Modifications:
#	14/04/2008	Allow day ranges for forecast data
#	14/04/2008	Check for connectivity to xoap service
#	18/04/2008	Allow the setting of spaces for ranged output
#	18/04/2008	Allow Night and Day forecast output
#	18/04/2008	Support locale for condition code text "CC" option, awaiting spanish language translation
#	18/04/2008	Use pickling for class data rather than opening xml, this bypasses the need to interrogate cached data
#	19/04/2008	Added spanish condition text - Thanks Bruce M
#	19/04/2008	Added isnumeric check on all numeric output with units suffix
#	19/04/2008	Altered pickle file naming to include location code
#	19/04/2008	Added spanish week days conversion via locale
#	20/04/2008	Added decent command argument parser
#	20/04/2008	Added --shortweekday option, if given the day of week data type is shortened to 3 characters
#	21/04/2008	Fixed locale options for forecast output
#	21/04/2008	Added --template option to allow custom output using a single exec call :)
#	21/04/2008	Added --hideunits option to remove, for example, mph and C from output
#	23/04/2008	Removed --imperial option from template, this MUST be set as a standard option on the script call and not used in the template file.
#	23/04/2008	Readded --imperial option to template, enabling metric or imperial values per datatype. Note when using templates command line option will not work.
#	23/04/2008	Added output notifying user if the location given is bad
#	24/04/2008	Added handling for no connectivity, will revert to cached data now (erroring if no cache exists). Tests by trying to open xoap.weather.com
#	24/04/2008	Fixed Celsius to fahrenheit conversion
#	06/05/2008	Updated url used after webservice was updated
#	09/05/2008	Consolidated current condition and forecast data fetch into one call
#	09/05/2008	Added Sunrise and sunset to datatypes, these are specific to both current conditions and forecast data
#	09/05/2008	Added moon phase, barometer reading and barometer description to datatypes, these are only specific to current conditions and so are N/A in forecasted output
#	09/05/2008	Added unit conversions for barometer from mb to inches (imperial)
#   09/05/2008  Updated spanish condition text - Thanks Bruce M
#   10/05/2008  Added french locale data - Thanks benpaka
#   12/05/2008  Added new BF (bearing font) datatype to provide an arrow character (use with Arrow.ttf font) instead of NSEW output from WD (wind direction)
#   12/05/2008  Updated WD output to be locale specific, currently supports default english and spanish - Thanks Bruce M
#	18/05/2008	Added new MF (moon font) datatype to provide a moon font character (characters incorrect and no dedicated font yet).
#	21/05/2008	For current conditions the --datatype=LT option now displays "feels like" temperature rather than the current temperature
#
# TODO:
# Consolidate pkl files into one file/class
# Add a weather font based moon phase output based on moon icon data
# ??? Any more requirements out there?

import sys, os, socket, urllib2, datetime, time
from xml.dom import minidom
from stat import *
from optparse import OptionParser
import locale
import gettext
import pickle
from math import *

APP="conkyForecast.py"
DIR=os.path.dirname (__file__) + '/locale'
gettext.bindtextdomain(APP, DIR)
gettext.textdomain(APP)
_ = gettext.gettext

class CommandLineParser:

	parser = None

	def __init__(self):

		self.parser = OptionParser()
		self.parser.add_option("-l","--location", dest="location", default="UKXX0103", type="string", metavar="CODE", help=u"location code for weather data [default: %default],Use the following url to determine your location code by city name: http://xoap.weather.com/search/search?where=Norwich")
		self.parser.add_option("-d","--datatype",dest="datatype", default="HT", type="string", metavar="DATATYPE", help=u"[default: %default] The data type options are: DW (Day Of Week), WF (Weather Font Output), LT (Forecast:Low Temp,Current:Feels Like Temp), HT (Forecast:High Temp,Current:Current Temp), CC (Current Conditions), CT (Conditions Text), PC (Precipitation Chance), HM (Humidity), WD (Wind Direction), WS (Wind Speed), WG (Wind Gusts), CN (City Name), SR (sunrise), SS (sunset), MP (moon phase), MF (moon font), BR (barometer reading), BD (barometer description). Not applicable at command line when using templates.")
		self.parser.add_option("-s","--startday",dest="startday", type="int", metavar="NUMBER", help=u"define the starting day number, if omitted current conditions are output. Not applicable at command line when using templates.")
		self.parser.add_option("-e","--endday",dest="endday", type="int", metavar="NUMBER", help=u"define the ending day number, if omitted only starting day data is output. Not applicable at command line when using templates.")
		self.parser.add_option("-S","--spaces",dest="spaces", type="int", default=1, metavar="NUMBER", help=u"[default: %default] Define the number of spaces between ranged output. Not applicable at command line when using templates.")
		self.parser.add_option("-t","--template",dest="template", type="string", metavar="FILE", help=u"define a template file to generate output in one call. A displayable item in the file is in the form {--datatype=HT --startday=1}. The following are possible options within each item: --datatype,--startday,--endday,--night,--shortweekday,--imperial,--hideunits,--spaces . Note that the short forms of the options are not currently supported! None of these options are applicable at command line when using templates.")
		self.parser.add_option("-L","--locale",dest="locale", type="string", help=u"override the system locale for language output (en=english, es=spanish, fr=french, more to come)")
		self.parser.add_option("-i","--imperial",dest="imperial", default=False, action="store_true", help=u"request imperial units, if omitted output is in metric. Not applicable at command line when using templates.")
		self.parser.add_option("-n","--night",dest="night", default=False, action="store_true", help=u"switch output to night data, if omitted day output will be output. Not applicable at command line when using templates.")
		self.parser.add_option("-w","--shortweekday",dest="shortweekday", default=False, action="store_true", help=u"Shorten the day of week data type to 3 characters. Not applicable at command line when using templates.")
		self.parser.add_option("-u","--hideunits",dest="hideunits", default=False, action="store_true", help=u"Hide units such as mph or C, degree symbols (°) are still shown. Not applicable at command line when using templates.")
		self.parser.add_option("-v","--verbose",dest="verbose", default=False, action="store_true", help=u"request verbose output, no a good idea when running through conky!")
		self.parser.add_option("-r","--refetch",dest="refetch", default=False, action="store_true", help=u"fetch data regardless of data expiry")

	def parse_args(self):
		(options, args) = self.parser.parse_args()
		return (options, args)

	def print_help(self):
		return self.parser.print_help()

class WeatherData:
	def __init__(self, day_of_week, low, high, condition_code, condition_text, precip, humidity, wind_dir, wind_speed, wind_gusts, city, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc):
		self.day_of_week = u""+day_of_week
		self.low = u""+low
		self.high = u""+high
		self.condition_code = u""+condition_code
		self.condition_text = u""+condition_text
		self.precip = u""+precip
		self.humidity = u""+humidity
		self.wind_dir = u""+wind_dir
		self.wind_speed = u""+wind_speed
		self.wind_gusts = u""+wind_gusts
		self.city = u""+city
		self.sunrise = u""+sunrise
		self.sunset = u""+sunset
		self.moon_phase = u""+moon_phase
		self.moon_icon = u""+moon_icon
		self.bar_read = u""+bar_read
		self.bar_desc = u""+bar_desc


class WeatherText:

	conditions_text = {
		"0": _(u"Tornado"),
		"1": _(u"Tropical Storm"),
		"2": _(u"Hurricane"),
		"3": _(u"Severe Thunderstorms"),
		"4": _(u"Thunderstorms"),
		"5": _(u"Mixed Rain and Snow"),
		"6": _(u"Mixed Rain and Sleet"),
		"7": _(u"Mixed Precipitation"),
		"8": _(u"Freezing Drizzle"),
		"9": _(u"Drizzle"),
		"10": _(u"Freezing Rain"),
		"11": _(u"Showers"),
		"12": _(u"Showers"),
		"13": _(u"Snow Flurries"),
		"14": _(u"Light Snow Showers"),
		"15": _(u"Blowing Snow"),
		"16": _(u"Snow"),
		"17": _(u"Hail"),
		"18": _(u"Sleet"),
		"19": _(u"Dust"),
		"20": _(u"Fog"),
		"21": _(u"Haze"),
		"22": _(u"Smoke"),
		"23": _(u"Blustery"),
		"24": _(u"Windy"),
		"25": _(u"Cold"),
		"26": _(u"Cloudy"),
		"27": _(u"Mostly Cloudy"),
		"28": _(u"Mostly Cloudy"),
		"29": _(u"Partly Cloudy"),
		"30": _(u"Partly Cloudy"),
		"31": _(u"Clear"),
		"32": _(u"Clear"),
		"33": _(u"Fair"),
		"34": _(u"Fair"),
		"35": _(u"Mixed Rain and Hail"),
		"36": _(u"Hot"),
		"37": _(u"Isolated Thunderstorms"),
		"38": _(u"Scattered Thunderstorms"),
		"39": _(u"Scattered Thunderstorms"),
		"40": _(u"Scattered Showers"),
		"41": _(u"Heavy Snow"),
		"42": _(u"Scattered Snow Showers"),
		"43": _(u"Heavy Snow"),
		"44": _(u"Partly Cloudy"),
		"45": _(u"Thunder Showers"),
		"46": _(u"Snow Showers"),
		"47": _(u"Isolated Thunderstorms"),
		"na": _(u"N/A"),
		"-": _(u"N/A")
	}

	conditions_text_es = {
        "0": _(u"Tornado"),
        "1": _(u"Tormenta Tropical"),
        "2": _(u"Huracá¡n"),
        "3": _(u"Tormentas Fuertes"),
        "4": _(u"Tormentas"),
        "5": _(u"Lluvia y Nieve Mezclada"),
        "6": _(u"Lluvia y Aguanieve Mezclada"),
        "7": _(u"Aguanieve"),
        "8": _(u"Llovizna Helada"),
        "9": _(u"Llovizna"),
        "10": _(u"Lluvia Engelante"), # o lluvia helada
        "11": _(u"Chaparrones"),
        "12": _(u"Chaparrones"),
        "13": _(u"Nieve Ligera"),
        "14": _(u"Nieve Ligera"),
        "15": _(u"Ventisca de Nieve"),
        "16": _(u"Nieve"),
        "17": _(u"Granizo"),
        "18": _(u"Aguanieve"),
        "19": _(u"Polvo"),
        "20": _(u"Niebla"),
        "21": _(u"Bruma"),
        "22": _(u"Humo"),
        "23": _(u"Tempestad"),
        "24": _(u"Ventoso"),
        "25": _(u"Fráo"),
        "26": _(u"Muy Nublado"),
        "27": _(u"Principalmente Nublado"),
        "28": _(u"Principalmente Nublado"),
        "29": _(u"Parcialmente Nublado"),
        "30": _(u"Parcialmente Nublado"),
        "31": _(u"Despejado"),
        "32": _(u"Despejado"),
        "33": _(u"Algo Nublado"),
        "34": _(u"Algo Nublado"),
        "35": _(u"Lluvia con Granizo"),
        "36": _(u"Calor"),
        "37": _(u"Tormentas Aisladas"),
        "38": _(u"Tormentas Dispersas"),
        "39": _(u"Tormentas Dispersas"),
        "40": _(u"Chubascos Dispersos"),
        "41": _(u"Nieve Pesada"),
        "42": _(u"Nevadas Débiles y Dispersas"),
        "43": _(u"Nevada Intensa"),
        "44": _(u"Nubes Dispersas"),
        "45": _(u"Tormentas"),
        "46": _(u"Nevadas Dispersas"),
        "47": _(u"Tormentas Aisladas"),
        "na": _(u"N/A"),
        "-": _(u"N/A")
    }

	conditions_text_fr = {
        "0": _(u"Tornade"),
        "1": _(u"Tempête Tropicale"),
        "2": _(u"Ouragan"),
        "3": _(u"Orages Violents"),
        "4": _(u"Orageux"),
        "5": _(u"Pluie et Neige"),
        "6": _(u"Pluie et Neige Mouillée"),
        "7": _(u"Variable avec averses"),
        "8": _(u"Bruine Givrante"),
        "9": _(u"Bruine"),
        "10": _(u"Pluie Glacante"),
        "11": _(u"Averses"),
        "12": _(u"Averses"),
        "13": _(u"Légère Neige"),
        "14": _(u"Forte Neige"),
        "15": _(u"Tempête de Neige"),
        "16": _(u"Neige"),
        "17": _(u"Grêle"),
        "18": _(u"Pluie/Neige"),
        "19": _(u"Nuage de poussière"),
        "20": _(u"Brouillard"),
        "21": _(u"Brume"),
        "22": _(u"Fumée"),
        "23": _(u"Tres Venteux"),
        "24": _(u"Venteux"),
        "25": _(u"Froid"),
        "26": _(u"Nuageux"),
        "27": _(u"Tres Nuageux"),
        "28": _(u"Tres Nuageux"),
        "29": _(u"Nuages Disséminés"),
        "30": _(u"Nuages Disséminés"),
        "31": _(u"Beau"),
        "32": _(u"Beau"),
        "33": _(u"Belles Éclaircies"),
        "34": _(u"Belles Éclaircies"),
        "35": _(u"Pluie avec Grêle"),
        "36": _(u"Chaleur"),
        "37": _(u"Orages Isolés"),
        "38": _(u"Orages Localisés"),
        "39": _(u"Orages Localisés"),
        "40": _(u"Averses Localisées"),
        "41": _(u"Neige Lourde"),
        "42": _(u"Tempête de Neige Localisées"),
        "43": _(u"Neige Lourde"),
        "44": _(u"Nuages Disséminés"),
        "45": _(u"Orages"),
        "46": _(u"Tempête de Neige"),
        "47": _(u"Orages Isolés"),
        "na": _(u"N/A"),
        "-": _(u"N/A")
	}

	conditions_weather_font = {
		"0": _(u"W"),
		"1": _(u"V"),
		"2": _(u"W"),
		"3": _(u"s"),
		"4": _(u"p"),
		"5": _(u"k"),
		"6": _(u"k"),
		"7": _(u"g"),
		"8": _(u"g"),
		"9": _(u"g"),
		"10": _(u"h"),
		"11": _(u"g"),
		"12": _(u"g"),
		"13": _(u"k"),
		"14": _(u"k"),
		"15": _(u"k"),
		"16": _(u"k"),
		"17": _(u"k"),
		"18": _(u"k"),
		"19": _(u"e"),
		"20": _(u"e"),
		"21": _(u"a"),
		"22": _(u"d"),
		"23": _(u"d"),
		"24": _(u"d"),
		"25": _(u"d"),
		"26": _(u"e"),
		"27": _(u"e"),
		"28": _(u"e"),
		"29": _(u"c"),
		"30": _(u"c"),
		"31": _(u"a"),
		"32": _(u"a"),
		"33": _(u"b"),
		"34": _(u"b"),
		"35": _(u"k"),
		"36": _(u"a"),
		"37": _(u"f"),
		"38": _(u"f"),
		"39": _(u"f"),
		"40": _(u"g"),
		"41": _(u"k"),
		"42": _(u"k"),
		"43": _(u"k"),
		"44": _(u"b"),
		"45": _(u"g"),
		"46": _(u"k"),
		"47": _(u"f"),
		"na": _(u""),
		"-": _(u"")
	}

	conditions_moon_font = {
		"0": _(u"1"),
		"1": _(u"N"),
		"2": _(u"O"),
		"3": _(u"P"),
		"4": _(u"Q"),
		"5": _(u"R"),
		"6": _(u"S"),
		"7": _(u"T"),
		"8": _(u"U"),
		"9": _(u"V"),
		"10": _(u"W"),
		"11": _(u"X"),
		"12": _(u"Y"),
		"13": _(u"Z"),
		"14": _(u"0"),
		"15": _(u"0"),
		"16": _(u"A"),
		"17": _(u"B"),
		"18": _(u"C"),
		"19": _(u"D"),
		"20": _(u"E"),
		"21": _(u"F"),
		"22": _(u"G"),
		"23": _(u"H"),
		"24": _(u"I"),
		"25": _(u"J"),
		"26": _(u"K"),
		"27": _(u"L"),
		"28": _(u"M"),
		"29": _(u"1"),
		"na": _(u""),
		"-": _(u"")
	}

	day_of_week = {
		"Today": _(u"Today"),
		"Monday": _(u"Monday"),
		"Tuesday": _(u"Tuesday"),
		"Wednesday": _(u"Wednesday"),
		"Thursday": _(u"Thursday"),
		"Friday": _(u"Friday"),
		"Saturday": _(u"Saturday"),
		"Sunday": _(u"Sunday")
	}

	day_of_week_short = {
		"Today": _(u"Now"),
		"Monday": _(u"Mon"),
		"Tuesday": _(u"Tue"),
		"Wednesday": _(u"Wed"),
		"Thursday": _(u"Thu"),
		"Friday": _(u"Fri"),
		"Saturday": _(u"Sat"),
		"Sunday": _(u"Sun")
	}

	day_of_week_es = {
		"Today": _(u"hoy"),
		"Monday": _(u"lunes"),
		"Tuesday": _(u"martes"),
		"Wednesday": _(u"miércoles"),
		"Thursday": _(u"jueves"),
		"Friday": _(u"viernes"),
		"Saturday": _(u"sábado"),
		"Sunday": _(u"domingo")
	}

	day_of_week_short_es = {
		"Today": _(u"hoy"),
		"Monday": _(u"lun"),
		"Tuesday": _(u"mar"),
		"Wednesday": _(u"mié"),
		"Thursday": _(u"jue"),
		"Friday": _(u"vie"),
		"Saturday": _(u"sáb"),
		"Sunday": _(u"dom")
	}

	day_of_week_fr = {
		"Today": _(u"Aujourd'hui"),
		"Monday": _(u"Lundi"),
		"Tuesday": _(u"Mardi"),
		"Wednesday": _(u"Mercredi"),
		"Thursday": _(u"Jeudi"),
		"Friday": _(u"Vendredi"),
		"Saturday": _(u"Samedi"),
		"Sunday": _(u"Dimanche")
	}

	day_of_week_short_fr = {
		"Today": _(u"Auj"),
		"Monday": _(u"Lun"),
		"Tuesday": _(u"Mar"),
		"Wednesday": _(u"Mer"),
		"Thursday": _(u"Jeu"),
		"Friday": _(u"Ven"),
		"Saturday": _(u"Sam"),
		"Sunday": _(u"Dim")
	}

	bearing_arrow_font = {
		"N": _(u"i"),
		"NNE": _(u"j"),
		"NE": _(u"k"),
		"ENE": _(u"l"),
		"E": _(u"m"),
		"ESE": _(u"n"),
		"SE": _(u"o"),
		"SSE": _(u"p"),
		"S": _(u"a"),
		"SSW": _(u"b"),
		"SW": _(u"c"),
		"WSW": _(u"d"),
		"W": _(u"e"),
		"WNW": _(u"f"),
		"NW": _(u"g"),
		"NNW": _(u"h"),
		"N/A": _(u" ")
	}

	bearing_text_es = {
		"N": _(u"N"),
		"NNE": _(u"NNE"),
		"NE": _(u"NE"),
		"ENE": _(u"ENE"),
		"E": _(u"E"),
		"ESE": _(u"ESE"),
		"SE": _(u"SE"),
		"SSE": _(u"SSE"),
		"S": _(u"S"),
		"SSW": _(u"SSO"),
		"SW": _(u"SO"),
		"WSW": _(u"WOW"),
		"W": _(u"O"),
		"WNW": _(u"ONO"),
		"NW": _(u"NO"),
		"NNW": _(u"NNO"),
		"N/A": _(u"N\A")
	}

	bearing_text_fr = {
		"N": _(u"N"),
		"NNE": _(u"NNE"),
		"NE": _(u"NE"),
		"ENE": _(u"ENE"),
		"E": _(u"E"),
		"ESE": _(u"ESE"),
		"SE": _(u"SE"),
		"SSE": _(u"SSE"),
		"S": _(u"S"),
		"SSW": _(u"SSO"),
		"SW": _(u"SO"),
		"WSW": _(u"WOW"),
		"W": _(u"O"),
		"WNW": _(u"ONO"),
		"NW": _(u"NO"),
		"NNW": _(u"NNO"),
		"N/A": _(u"N\A")
	}

class GlobalWeather:

	current_conditions = []
	day_forecast = []
	night_forecast = []

	locale = "en"

	options = None
	weatherxmldoc = ""

 	TEMP_FILEPATH_CURRENT = "/tmp/conkyForecast-c-LOCATION.pkl"
	TEMP_FILEPATH_DAYFORECAST = "/tmp/conkyForecast-df-LOCATION.pkl"
	TEMP_FILEPATH_NIGHTFORECAST = "/tmp/conkyForecast-nf-LOCATION.pkl"
 	EXPIRY_MINUTES = 30
	DEFAULT_SPACING = u" "


	def __init__(self,options):

		self.options = options

		if self.options.locale == None:
			try:
				#self.locale = locale.getdefaultlocale()[0][0:2]
				self.locale = "es" #uncomment this line to force Spanish locale
				#self.locale = "fr" #uncomment this line to force French locale
			except:
				print "locale not set"
		else:
			#self.locale = self.options.locale
			self.locale = "es" #uncomment this line to force Spanish locale
			#self.locale = "fr" #uncomment this line to force French locale

		if self.options.verbose == True:
			print >> sys.stdout, "locale set to ",self.locale

	def getText(self,nodelist):
		rc = ""
		for node in nodelist:
			if node.nodeType == node.TEXT_NODE:
				rc = rc + node.data
		return rc


	def getSpaces(self,spaces):
		string = u""
		if spaces == None:
			string = self.DEFAULT_SPACING
		else:
			for i in range(0, spaces+1):
				string = string + u" "
		return string


	def isNumeric(self,string):
		try:
			dummy = float(string)
			return True
		except:
			return False

	def isConnectionAvailable(self):
		# ensure we can access weather.com's server by opening the url
		try:
			usock = urllib2.urlopen('http://xoap.weather.com')
			usock.close()
			return True
		except:
			return False

	def getBearingText(self,bearing):
		bearing = float(bearing)
		if bearing < 11.25:
			return u"N"
		elif bearing < 33.75:
			return u"NNE"
		elif bearing < 56.25:
			return u"NE"
		elif bearing < 78.75:
			return u"ENE"
		elif bearing < 101.25:
			return u"E"
		elif bearing < 123.75:
			return u"ESE"
		elif bearing < 146.25:
			return u"SE"
		elif bearing < 168.75:
			return u"SSE"
		elif bearing < 191.25:
			return u"S"
		elif bearing < 213.75:
			return u"SSW"
		elif bearing < 236.25:
			return u"SW"
		elif bearing < 258.75:
			return u"WSW"
		elif bearing < 281.25:
			return u"W"
		elif bearing < 303.75:
			return u"WNW"
		elif bearing < 326.25:
			return u"NW"
		elif bearing < 348.75:
			return u"NNW"
		else:
			return "N/A"

	def convertCelsiusToFahrenheit(self,temp):
		return str(int(floor(((float(temp)*9.0)/5.0)+32)))

	def convertKilometresToMiles(self,dist):
		return str(int(floor(float(dist)*0.621371192)))

	def convertMillibarsToInches(self,mb):
		return str(int(floor(float(mb)/33.8582)))

	def getTemplateList(self,template):

		templatelist = []

		for template_part in template.split("{"):
			if template_part != "":
				for template_part in template_part.split("}"):
					if template_part != "":
						templatelist.append(u""+template_part)

		return templatelist


	def getOutputText(self,datatype,startday,endday,night,shortweekday,imperial,hideunits,spaces):
		#try:
			output = u""

			# define current units for output
			if hideunits == False:
				if imperial == False:
					tempunit = u"°C"
					speedunit = u"kph"
					pressureunit = u"mb"
				else:
					tempunit = u"°F"
					speedunit = u"mph"
					pressureunit = u"in"
			else:
				tempunit = u"°"
				speedunit = u""
				pressureunit = u""

			if startday == None: # current conditions

				if datatype == "DW":
					if self.locale == "es":
						if shortweekday == True:
							output = WeatherText.day_of_week_short_es[self.current_conditions[0].day_of_week]
						else:
							output = WeatherText.day_of_week_es[self.current_conditions[0].day_of_week]
					elif self.locale == "fr":
						if shortweekday == True:
							output = WeatherText.day_of_week_short_fr[self.current_conditions[0].day_of_week]
						else:
							output = WeatherText.day_of_week_fr[self.current_conditions[0].day_of_week]
					else:
						if shortweekday == True:
							output = WeatherText.day_of_week_short[self.current_conditions[0].day_of_week]
						else:
							output = WeatherText.day_of_week[self.current_conditions[0].day_of_week]
				elif datatype == "WF": # weather font
					output = WeatherText.conditions_weather_font[self.current_conditions[0].condition_code]
				elif datatype == "LT":
					string = self.current_conditions[0].low
					if self.isNumeric(string) == True:
						if imperial == True:
							string = self.convertCelsiusToFahrenheit(string)
						string = string + tempunit
					output = string
				elif datatype == "HT":
					string = self.current_conditions[0].high
					if self.isNumeric(string) == True:
						if imperial == True:
							string = self.convertCelsiusToFahrenheit(string)
						string = string + tempunit
					output = string
				elif datatype == "CC":
					if self.locale == "es":
						output = WeatherText.conditions_text_es[self.current_conditions[0].condition_code]
					elif self.locale == "fr":
						output = WeatherText.conditions_text_fr[self.current_conditions[0].condition_code]
					else:
						output = WeatherText.conditions_text[self.current_conditions[0].condition_code]
				elif datatype == "CT":
					output = self.current_conditions[0].condition_text
				elif datatype == "PC":
					string = self.current_conditions[0].precip
					if self.isNumeric(string) == True:
						string = string + u"%"
					output = string
				elif datatype == "HM":
					string = self.current_conditions[0].humidity
					if self.isNumeric(string) == True:
						string = string + u"%"
					output = string
				elif datatype == "WD":
					string = self.current_conditions[0].wind_dir
					if self.isNumeric(string) == True:
						string = self.getBearingText(string)

					if self.locale == "es":
						output = WeatherText.bearing_text_es[string]
					elif self.locale == "fr":
						output = WeatherText.bearing_text_fr[string]
					else:
						output = string

				elif datatype == "BF":
					string = self.current_conditions[0].wind_dir
					if self.isNumeric(string) == True:
						string = WeatherText.bearing_arrow_font[self.getBearingText(string)]
					output = string
				elif datatype == "WS":
					string = self.current_conditions[0].wind_speed
					if self.isNumeric(string) == True:
						if imperial == True:
							string = self.convertKilometresToMiles(string)
						string = string + speedunit
					output = string
				elif datatype == "WG":
					string = self.current_conditions[0].wind_gusts
					if self.isNumeric(string) == True:
						if imperial == True:
							string = self.convertKilometresToMiles(string)
						string = string + speedunit
					output = string
				elif datatype == "CN":
					output = self.current_conditions[0].city
				elif datatype == "SR":
					output = self.current_conditions[0].sunrise
				elif datatype == "SS":
					output = self.current_conditions[0].sunset
				elif datatype == "MP":
					output = self.current_conditions[0].moon_phase
				elif datatype == "MF":
					output = WeatherText.conditions_moon_font[self.current_conditions[0].moon_icon]
				elif datatype == "BR":
					string = self.current_conditions[0].bar_read
					if self.isNumeric(string) == True:
						if imperial == True:
							string = self.convertMillibarsToInches(string)
						string = string + pressureunit
					output = string
				elif datatype == "BD":
					output = self.current_conditions[0].bar_desc
				else:
					output = "\nERROR:Unknown data type requested"

			else: # forecast data

				if endday == None: # if no endday was set use startday
					endday = startday

				if night == True: # night forecast required

					for day_number in range(startday, endday+1):

						if datatype == "DW":
							if self.locale == "es":
								if shortweekday == True:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_short_es[self.night_forecast[day_number].day_of_week]
								else:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_es[self.night_forecast[day_number].day_of_week]
							elif self.locale == "fr":
								if shortweekday == True:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_short_fr[self.night_forecast[day_number].day_of_week]
								else:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_fr[self.night_forecast[day_number].day_of_week]
							else:
								if shortweekday == True:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_short[self.night_forecast[day_number].day_of_week]
								else:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week[self.night_forecast[day_number].day_of_week]
						elif datatype == "WF": # weather font
							output = output + self.getSpaces(spaces) + WeatherText.conditions_weather_font[self.night_forecast[day_number].condition_code]
						elif datatype == "LT":
							string = self.night_forecast[day_number].low
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertCelsiusToFahrenheit(string)
								string = string + tempunit
							output = output + self.getSpaces(spaces) + string

						elif datatype == "HT":
							string = self.night_forecast[day_number].high
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertCelsiusToFahrenheit(string)
								string = string + tempunit
							output = output + self.getSpaces(spaces) + string
						elif datatype == "CC":
							if self.locale == "es":
								output = output + self.getSpaces(spaces) + WeatherText.conditions_text_es[self.night_forecast[day_number].condition_code]
							elif self.locale == "fr":
								output = output + self.getSpaces(spaces) + WeatherText.conditions_text_fr[self.night_forecast[day_number].condition_code]
							else:
								output = output + self.getSpaces(spaces) + WeatherText.conditions_text[self.night_forecast[day_number].condition_code]
						elif datatype == "CT":
							output = output + self.getSpaces(spaces) + self.night_forecast[day_number].condition_text
						elif datatype == "PC":
							string = self.night_forecast[day_number].precip
							if self.isNumeric(string) == True:
								string = string + u"%"
							output = output + self.getSpaces(spaces) + string
						elif datatype == "HM":
							string = self.night_forecast[day_number].humidity
							if self.isNumeric(string) == True:
								string = string + u"%"
							output = output + self.getSpaces(spaces) + string
						elif datatype == "WD":
							string = self.night_forecast[day_number].wind_dir
							if self.locale == "es":
								output = output + self.getSpaces(spaces) + WeatherText.bearing_text_es[string]
							elif self.locale == "fr":
								output = output + self.getSpaces(spaces) + WeatherText.bearing_text_fr[string]
							else:
								output = output + self.getSpaces(spaces) + string

						elif datatype == "BF":
							output = output + self.getSpaces(spaces) + WeatherText.bearing_arrow_font[self.night_forecast[day_number].wind_dir]
						elif datatype == "WS":
							string = self.night_forecast[day_number].wind_speed
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertKilometresToMiles(string)
								string = string + speedunit
							output = output + self.getSpaces(spaces) + string
						elif datatype == "WG":
							string = self.night_forecast[day_number].wind_gusts
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertKilometresToMiles(string)
								string = string + speedunit
							output = output + self.getSpaces(spaces) + string
						elif datatype == "CN":
							output = output + self.getSpaces(spaces) + self.night_forecast[day_number].city
						elif datatype == "SR":
							output = output + self.getSpaces(spaces) + self.night_forecast[day_number].sunrise
						elif datatype == "SS":
							output = output + self.getSpaces(spaces) + self.night_forecast[day_number].sunset
						elif datatype == "MP":
							output = output + self.getSpaces(spaces) + self.night_forecast[day_number].moon_phase
						elif datatype == "MF":
							output = output + self.getSpaces(spaces) + WeatherText.conditions_moon_font[self.night_forecast[day_number].moon_icon]
						elif datatype == "BR":
							output = output + self.getSpaces(spaces) + self.night_forecast[day_number].bar_read
						elif datatype == "BD":
							output = output + self.getSpaces(spaces) + self.night_forecast[day_number].bar_desc
						else:
							output = "\nERROR:Unknown data type requested"
							break

				else: # day forecast wanted

					for day_number in range(startday, endday+1):

						if datatype == "DW":
							if self.locale == "es":
								if shortweekday == True:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_short_es[self.day_forecast[day_number].day_of_week]
								else:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_es[self.day_forecast[day_number].day_of_week]
							elif self.locale == "fr":
								if shortweekday == True:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_short_fr[self.day_forecast[day_number].day_of_week]
								else:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_fr[self.day_forecast[day_number].day_of_week]
							else:
								if shortweekday == True:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_short[self.day_forecast[day_number].day_of_week]
								else:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week[self.day_forecast[day_number].day_of_week]
						elif datatype == "WF": # weather font
							output = output + self.getSpaces(spaces) + WeatherText.conditions_weather_font[self.day_forecast[day_number].condition_code]
						elif datatype == "LT":
							string = self.day_forecast[day_number].low
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertCelsiusToFahrenheit(string)
								string = string + tempunit
							output = output + self.getSpaces(spaces) + string
						elif datatype == "HT":
							string = self.day_forecast[day_number].high
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertCelsiusToFahrenheit(string)
								string = string + tempunit
							output = output + self.getSpaces(spaces) + string
						elif datatype == "CC":
							if self.locale == "es":
								output = output + self.getSpaces(spaces) + WeatherText.conditions_text_es[self.day_forecast[day_number].condition_code]
							elif self.locale == "fr":
								output = output + self.getSpaces(spaces) + WeatherText.conditions_text_fr[self.day_forecast[day_number].condition_code]
							else:
								output = output + self.getSpaces(spaces) + WeatherText.conditions_text[self.day_forecast[day_number].condition_code]
						elif datatype == "CT":
							output = output + self.getSpaces(spaces) + self.day_forecast[day_number].condition_text
						elif datatype == "PC":
							string = self.day_forecast[day_number].precip
							if self.isNumeric(string) == True:
								string = string + u"%"
							output = output + self.getSpaces(spaces) + string
						elif datatype == "HM":
							string = self.day_forecast[day_number].humidity
							if self.isNumeric(string) == True:
								string = string + u"%"
							output = output + self.getSpaces(spaces) + string
						elif datatype == "WD":
							string = self.day_forecast[day_number].wind_dir

							if self.locale == "es":
								output = output + self.getSpaces(spaces) + WeatherText.bearing_text_es[string]
							elif self.locale == "fr":
								output = output + self.getSpaces(spaces) + WeatherText.bearing_text_fr[string]
							else:
								output = output + self.getSpaces(spaces) + string

						elif datatype == "BF":
							output = output + self.getSpaces(spaces) + WeatherText.bearing_arrow_font[self.day_forecast[day_number].wind_dir]
						elif datatype == "WS":
							string = self.day_forecast[day_number].wind_speed
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertKilometresToMiles(string)
								string = string + speedunit
							output = output + self.getSpaces(spaces) + string
						elif datatype == "WG":
							string = self.day_forecast[day_number].wind_gusts
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertKilometresToMiles(string)
								string = string + speedunit
							output = output + self.getSpaces(spaces) + string
						elif datatype == "CN":
							output = output + self.getSpaces(spaces) + self.day_forecast[day_number].city
						elif datatype == "SR":
							output = output + self.getSpaces(spaces) + self.day_forecast[day_number].sunrise
						elif datatype == "SS":
							output = output + self.getSpaces(spaces) + self.day_forecast[day_number].sunset
						elif datatype == "MP":
							output = output + self.getSpaces(spaces) + self.day_forecast[day_number].moon_phase
						elif datatype == "MF":
							output = output + self.getSpaces(spaces) + WeatherText.conditions_moon_font[self.day_forecast[day_number].moon_icon]
						elif datatype == "BR":
							output = output + self.getSpaces(spaces) + self.day_forecast[day_number].bar_read
						elif datatype == "BD":
							output = output + self.getSpaces(spaces) + self.day_forecast[day_number].bar_desc
						else:
							output = u"\nERROR:Unknown data type requested"
							break

			output = u""+output.strip(u" ") # lose leading/trailing spaces
			return output

		#except:
			#print "getOutputText:Unexpected error: ", sys.exc_info()[0]


	def getOutputTextFromTemplate(self,template):
		#try:

			# keys to template data
			DATATYPE_KEY = "--datatype="
			STARTDAY_KEY = "--startday="
			ENDDAY_KEY = "--endday="
			NIGHT_KEY = "--night"
			SHORTWEEKDAY_KEY = "--shortweekday"
			IMPERIAL_KEY = "--imperial"
			HIDEUNITS_KEY = "--hideunits"
			SPACES_KEY = "--spaces="

			output = u""

			optionfound = False

			#load the file
			try:
				fileinput = open(self.options.template)
				template = fileinput.read()
				fileinput.close()
			except:
				output = u"Template file no found!"

			templatelist = self.getTemplateList(template)

			# lets walk through the template list and determine the output for each item found
			for i in range(0,len(templatelist)-1):

				pos = templatelist[i].find(DATATYPE_KEY)
				if pos != -1:
					optionfound = True
					pos = pos + len(DATATYPE_KEY)
					datatype = templatelist[i][pos:pos+4].strip("}").strip("{").strip("-").strip(" ")
				else:
					datatype = None

				pos = templatelist[i].find(STARTDAY_KEY)
				if pos != -1:
					optionfound = True
					pos = pos + len(STARTDAY_KEY)
					startday = int(templatelist[i][pos:pos+4].strip("}").strip("{").strip("-").strip(" "))
				else:
					startday = None

				pos = templatelist[i].find(ENDDAY_KEY)
				if pos != -1:
					optionfound = True
					pos = pos + len(ENDDAY_KEY)
					endday = int(templatelist[i][pos:pos+4].strip("}").strip("{").strip("-").strip(" "))
				else:
					endday = None

				pos = templatelist[i].find(NIGHT_KEY)
				if pos != -1:
					optionfound = True
					night = True
				else:
					night = False

				pos = templatelist[i].find(SHORTWEEKDAY_KEY)
				if pos != -1:
					optionfound = True
					shortweekday = True
				else:
					shortweekday = False

				pos = templatelist[i].find(IMPERIAL_KEY)
				if pos != -1:
					optionfound = True
					imperial = True
				else:
					imperial = False

				pos = templatelist[i].find(HIDEUNITS_KEY)
				if pos != -1:
					optionfound = True
					hideunits = True
				else:
					hideunits = False

				pos = templatelist[i].find(SPACES_KEY)
				if pos != -1:
					optionfound = True
					pos = pos + len(SPACES_KEY)
					spaces = int(templatelist[i][pos:pos+4].strip("}").strip("{").strip("-").strip(" "))
				else:
					spaces = 1

				if optionfound == True:
					templatelist[i] = self.getOutputText(datatype,startday,endday,night,shortweekday,imperial,hideunits,spaces)
					optionfound = False

			# go through the list concatenating the output now that it's been populated
			for item in templatelist:
				output = output + item

			return output

		#except:
			#print "getOutputTextFromTemplate:Unexpected error: ", sys.exc_info()[0]


	def fetchData(self):

		# always fetch metric data, use conversation functions on this data
		file_path_current = self.TEMP_FILEPATH_CURRENT.replace("LOCATION",self.options.location)
		file_path_dayforecast = self.TEMP_FILEPATH_DAYFORECAST.replace("LOCATION",self.options.location)
		file_path_nightforecast = self.TEMP_FILEPATH_NIGHTFORECAST.replace("LOCATION",self.options.location)

		if self.isConnectionAvailable() == False:
			if os.path.exists(file_path_current):
				RefetchData = False
			else: # no connection, no cache, bang!
				print "No internet connection is available and no cached weather data exists."
		elif self.options.refetch == True:
			RefetchData = True
		else:
	 		# does the data need retrieving again?
	 		if os.path.exists(file_path_current):
	 			lastmodDate = time.localtime(os.stat(file_path_current)[ST_MTIME])
				expiryDate = (datetime.datetime.today() - datetime.timedelta(minutes=self.EXPIRY_MINUTES)).timetuple()

				if expiryDate > lastmodDate:
					RefetchData = True
				else:
					RefetchData = False
			else:
				RefetchData = True


                # fetch the current conditions data, either from the website or by 'unpickling'
 		if RefetchData == True:

			# obtain current conditions data from xoap service
			try:

				# http://xoap.weather.com/weather/local/UKXX0103?cc=*&dayf=5&link=xoap&prod=xoap&par=1061785028&key=e374effbfd74930b

				url = 'http://xoap.weather.com/weather/local/' + self.options.location + '?cc=*&dayf=8&link=xoap&prod=xoap&par=1061785028&key=e374effbfd74930b&unit=m'
				if self.options.verbose == True:
					print >> sys.stdout, "fetching weather data from ",url

				usock = urllib2.urlopen(url)
				xml = usock.read()
				usock.close()
				self.weatherxmldoc = minidom.parseString(xml)
			except:
				print "fetchData:Unexpected error: ", sys.exc_info()[0]
				print "Unable to contact weather source for current conditions"

			# tell the user if the location is bad...
			found = xml.find("Invalid location provided")
			if found != -1:
				print "Invalid location provided"

			# interrogate weather data, load into class structure and pickle it
			try:

				# prepare weather data lists
				self.current_conditions = []
				self.day_forecast = []
				self.night_forecast = []

				# collect general data
				weather_n = self.weatherxmldoc.documentElement
				location_n = weather_n.getElementsByTagName('loc')[0]
				city_n = location_n.getElementsByTagName('dnam')[0]
				city = self.getText(city_n.childNodes)

				# collect current conditions data
				day_of_week = u"Today"
				precip = u"N/A"
				sunrise_n = location_n.getElementsByTagName('sunr')[0]
				sunrise = self.getText(sunrise_n.childNodes)
				sunset_n = location_n.getElementsByTagName('suns')[0]
				sunset = self.getText(sunset_n.childNodes)
				current_condition_n = weather_n.getElementsByTagName('cc')[0]
				current_desc_n = current_condition_n.getElementsByTagName('t')[0]
				current_desc = self.getText(current_desc_n.childNodes)
				current_code_n = current_condition_n.getElementsByTagName('icon')[0]
				current_code = self.getText(current_code_n.childNodes)
				current_temp_n = current_condition_n.getElementsByTagName('tmp')[0]
				current_temp = self.getText(current_temp_n.childNodes)
				current_temp_feels_n = current_condition_n.getElementsByTagName('flik')[0]
				current_temp_feels = self.getText(current_temp_feels_n.childNodes)
				bar_n = current_condition_n.getElementsByTagName('bar')[0]
				bar_read_n = bar_n.getElementsByTagName('r')[0]
				bar_read = self.getText(bar_read_n.childNodes)
				bar_desc_n = bar_n.getElementsByTagName('d')[0]
				bar_desc = self.getText(bar_desc_n.childNodes)
				wind_n = current_condition_n.getElementsByTagName('wind')[0]
				wind_speed_n = wind_n.getElementsByTagName('s')[0]
				wind_speed = self.getText(wind_speed_n.childNodes)
				wind_gust_n = wind_n.getElementsByTagName('gust')[0]
				wind_gusts = self.getText(wind_gust_n.childNodes)
				wind_dir_n = wind_n.getElementsByTagName('d')[0]
				wind_direction = self.getText(wind_dir_n.childNodes)
				humidity_n = current_condition_n.getElementsByTagName('hmid')[0]
				humidity = self.getText(humidity_n.childNodes)
				moon_n = current_condition_n.getElementsByTagName('moon')[0]
				moon_icon_n = moon_n.getElementsByTagName('icon')[0]
				moon_icon = self.getText(moon_icon_n.childNodes)
				moon_phase_n = moon_n.getElementsByTagName('t')[0]
				moon_phase = self.getText(moon_phase_n.childNodes)
				current_conditions_data = WeatherData(day_of_week, current_temp_feels, current_temp, current_code, current_desc, precip, humidity, wind_direction, wind_speed, wind_gusts, city, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc)
				self.current_conditions.append(current_conditions_data)

				# collect forecast data
				bar_read = u"N/A"
				bar_desc = u"N/A"
				moon_phase = u"N/A"
				moon_icon = u"na"
				forecast_n = weather_n.getElementsByTagName('dayf')[0]
				day_nodes = forecast_n.getElementsByTagName('day')

				for day in day_nodes:
					day_of_week = day.getAttribute('t')
					day_of_year = day.getAttribute('dt')
					high_temp_n = day.getElementsByTagName('hi')[0]
					high_temp = self.getText(high_temp_n.childNodes)
					low_temp_n = day.getElementsByTagName('low')[0]
					low_temp = self.getText(low_temp_n.childNodes)

					sunrise_n = day.getElementsByTagName('sunr')[0]
					sunrise = self.getText(sunrise_n.childNodes)
					sunset_n = day.getElementsByTagName('suns')[0]
					sunset = self.getText(sunset_n.childNodes)

					# day forecast specific data
					daytime_n = day.getElementsByTagName('part')[0] # day
					condition_code_n = daytime_n.getElementsByTagName('icon')[0]
					condition_code = self.getText(condition_code_n.childNodes)
					condition_n = daytime_n.getElementsByTagName('t')[0]
					condition = self.getText(condition_n.childNodes)
					precip_n = daytime_n.getElementsByTagName('ppcp')[0]
					precip = self.getText(precip_n.childNodes)
					humidity_n = daytime_n.getElementsByTagName('hmid')[0]
					humidity = self.getText(humidity_n.childNodes)
					wind_n = daytime_n.getElementsByTagName('wind')[0]
					wind_speed_n = wind_n.getElementsByTagName('s')[0]
					wind_speed = self.getText(wind_speed_n.childNodes)
					wind_direction_n = wind_n.getElementsByTagName('t')[0]
					wind_direction = self.getText(wind_direction_n.childNodes)
					wind_gusts_n = wind_n.getElementsByTagName('gust')[0]
					wind_gusts = self.getText(wind_gusts_n.childNodes)
					day_forecast_data = WeatherData(day_of_week, low_temp, high_temp, condition_code, condition, precip, humidity, wind_direction, wind_speed, wind_gusts, city, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc)
					self.day_forecast.append(day_forecast_data)

					# night forecast specific data
					daytime_n = day.getElementsByTagName('part')[1] # night
					condition_code_n = daytime_n.getElementsByTagName('icon')[0]
					condition_code = self.getText(condition_code_n.childNodes)
					condition_n = daytime_n.getElementsByTagName('t')[0]
					condition = self.getText(condition_n.childNodes)
					precip_n = daytime_n.getElementsByTagName('ppcp')[0]
					precip = self.getText(precip_n.childNodes)
					humidity_n = daytime_n.getElementsByTagName('hmid')[0]
					humidity = self.getText(humidity_n.childNodes)
					wind_n = daytime_n.getElementsByTagName('wind')[0]
					wind_speed_n = wind_n.getElementsByTagName('s')[0]
					wind_speed = self.getText(wind_speed_n.childNodes)
					wind_direction_n = wind_n.getElementsByTagName('t')[0]
					wind_direction = self.getText(wind_direction_n.childNodes)
					wind_gusts_n = wind_n.getElementsByTagName('gust')[0]
					wind_gusts = self.getText(wind_gusts_n.childNodes)
					night_forecast_data = WeatherData(day_of_week, low_temp, high_temp, condition_code, condition, precip, humidity, wind_direction, wind_speed, wind_gusts, city, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc)
					self.night_forecast.append(night_forecast_data)


				# pickle the data for next time!
				fileoutput = open(file_path_current, 'w')
 				pickle.dump(self.current_conditions,fileoutput)
		 		fileoutput.close()

				fileoutput = open(file_path_dayforecast, 'w')
 				pickle.dump(self.day_forecast,fileoutput)
		 		fileoutput.close()

				fileoutput = open(file_path_nightforecast, 'w')
 				pickle.dump(self.night_forecast,fileoutput)
		 		fileoutput.close()

			except:
				print "fetchData:Unexpected error: ", sys.exc_info()[0]
				print "Unable to interrogate the weather data"

		else: # fetch weather data from pickled class files
			if self.options.verbose == True:
				print >> sys.stdout, "fetching weather data from file: ",file_path_current

 			fileinput = open(file_path_current, 'r')
			self.current_conditions = pickle.load(fileinput)
			fileinput.close()

			if self.options.verbose == True:
				print >> sys.stdout, "fetching day forecast data from files: ",file_path_dayforecast, file_path_nightforecast

 			fileinput = open(file_path_dayforecast, 'r')
			self.day_forecast = pickle.load(fileinput)
			fileinput.close()

			if self.options.verbose == True:
				print >> sys.stdout, "fetching day forecast data from files: ",file_path_nightforecast, file_path_nightforecast

 			fileinput = open(file_path_nightforecast, 'r')
			self.night_forecast = pickle.load(fileinput)
			fileinput.close()

	def outputData(self):
		#try:

			if self.options.template != None:

				output = self.getOutputTextFromTemplate(self.options.template)

			else:

				output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)


			print output.encode("utf-8")

		#except:
			#print "outputData:Unexpected error: ", sys.exc_info()[0]

if __name__ == "__main__":

	parser = CommandLineParser()
	(options, args) = parser.parse_args()

	if options.verbose == True:
		print >> sys.stdout, "location:",options.location
		print >> sys.stdout, "imperial:",options.imperial
		print >> sys.stdout, "datatype:",options.datatype
		print >> sys.stdout, "night:",options.night
		print >> sys.stdout, "start day:",options.startday
		print >> sys.stdout, "end day:",options.endday
		print >> sys.stdout, "spaces:",options.spaces
		print >> sys.stdout, "verbose:",options.verbose
		print >> sys.stdout, "refetch:",options.refetch

	# create new global weather object
	weather = GlobalWeather(options)
	weather.fetchData()
	weather.outputData()


```
**PASO 7** Crear un archivo de ~/Conky/scripts/myweather.template
```
gedit ~/Conky/scripts/myweather.template
```
Este es mi archivo ~/Conky/scripts/myweather.template. Copia y pegalo en el archivo vacio que creates anteriormente con gedit. Luego guardalo.
```
{--datatype=DW --startday=1}:  {--datatype=CC --startday=1}
{--datatype=HT --startday=1} / {--datatype=LT --startday=1}   Viento del {--datatype=WD --startday=1}  a  {--datatype=WS --startday=1}
Humedad: {--datatype=HM --startday=1}          Precipitacion: {--datatype=PC --startday=1}
Salida del Sol: {--datatype=SR --startday=1}   Ocaso: {--datatype=SS --startday=1}
-----------------------------------------------
{--datatype=DW --startday=2}:  {--datatype=CC --startday=2}
{--datatype=HT --startday=2} / {--datatype=LT --startday=2}   Viento del {--datatype=WD --startday=2}  a  {--datatype=WS --startday=2}
Humedad: {--datatype=HM --startday=2}          Precipitacion: {--datatype=PC --startday=2}
Salida del Sol: {--datatype=SR --startday=2}   Ocaso: {--datatype=SS --startday=2}
-----------------------------------------------
{--datatype=DW --startday=3}:  {--datatype=CC --startday=3}
{--datatype=HT --startday=3} / {--datatype=LT --startday=3}   Viento del {--datatype=WD --startday=3}  a  {--datatype=WS --startday=3}
Humedad: {--datatype=HM --startday=3}          Precipitacion: {--datatype=PC --startday=3}
Salida del Sol: {--datatype=SR --startday=3}   Ocaso: {--datatype=SS --startday=3}
-----------------------------------------------
{--datatype=DW --startday=4}:  {--datatype=CC --startday=4}
{--datatype=HT --startday=4} / {--datatype=LT --startday=4}   Viento del {--datatype=WD --startday=4}  a  {--datatype=WS --startday=4}
Humedad: {--datatype=HM --startday=4}          Precipitacion: {--datatype=PC --startday=4}
Salida del Sol: {--datatype=SR --startday=4}   Ocaso: {--datatype=SS --startday=4}
```
**PASO 8** Crear un archivo de ~/Conky/scripts/mail/conkyEmail.py
```
gedit ~/Conky/scripts/mail/conkyEmail.py
```
Este es mi archivo ~/Conky/scripts/mail/conkyEmail.py. Copia y pegalo en el archivo vacio que creates anteriormente con gedit. Luego guardalo.
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
###############################################################################
# conkyEmail.py is a simple python script to gather 
# details of email inboxes use in conky.
#
#  Author: Kaivalagi
# Created: 16/05/2008
#
# TODO:
#  Implement something to understand what emails are new and what are already downloaded for pop3! Nasty!!
import sys, poplib, imaplib
from optparse import OptionParser

class CommandLineParser:

    parser = None

    def __init__(self):

        self.parser = OptionParser()
        self.parser.add_option("-m","--servertype", dest="servertype", default="POP", type="string", metavar="SERVERTYPE", help=u"servertype to check [default: %default] The server type options are POP or IMAP")
        self.parser.add_option("-s","--servername", dest="servername", default="pop.mail.yahoo.co.uk", type="string", metavar="SERVERNAME", help=u"server name to access [default: %default] The server name should be either a domain name or ip address")
        self.parser.add_option("-e","--ssl", dest="ssl", default=False, action="store_true", help=u"Use an SSL based connection.")
        self.parser.add_option("-u","--username",dest="username", type="string", metavar="USERNAME", help=u"username to login with")
        self.parser.add_option("-p","--password",dest="password", type="string", metavar="PASSWORD", help=u"Password to login with")
        self.parser.add_option("-t","--template",dest="template", type="string", metavar="FILE", help=u"define a template file to generate output in one call. A displayable item in the file is in the form {--servertype=POP --ssl --servername=pop.mail.yahoo.com --username=joebloggs --password=letmein}. Note that the short forms of the options are not currently supported! None of these options are applicable at command line when using templates.")
        self.parser.add_option("-v","--verbose",dest="verbose", default=False, action="store_true", help=u"request verbose output, not a good idea when running through conky!")

    def parse_args(self):
        (options, args) = self.parser.parse_args()
        return (options, args)

    def print_help(self):
        return self.parser.print_help()

class CheckEmail:

    def __init__(self,options):

        self.options = options

    def getTemplateList(self,template):

        templatelist = []
    
        for template_part in template.split("{"):
            if template_part != "":
                for template_part in template_part.split("}"):
                    if template_part != "":
                        templatelist.append(u""+template_part)

        return templatelist


    def getOutputText(self,servertype,servername,ssl,username,password):
        #try:
            output = u""
        
            if servertype == "POP":
                output = self.getPOPEmailCount(servername,ssl,username,password)
            elif servertype == "IMAP":
                output = self.getIMAPEmailCount(servername,ssl,username,password)
            else:
                output = "\nERROR:Unknown server type requested"

            output = u""+output.strip(u" ") # lose leading/trailing spaces
            return output

        #except:
            #print "getOutputText:Unexpected error: ", sys.exc_info()[0]


    def getOutputTextFromTemplate(self,template):
        #try:

            # keys to template data
            SERVERTYPE_KEY = "--servertype="
            SERVERNAME_KEY = "--servername="
            SSL_KEY= "--ssl"
            USERNAME_KEY = "--username="
            PASSWORD_KEY = "--password="

            output = u""

            optionfound = False

            #load the file
            try:
                fileinput = open(self.options.template)
                template = fileinput.read()
                fileinput.close()
            except:
                output = u"Template file no found!"

            templatelist = self.getTemplateList(template)

            # lets walk through the template list and determine the output for each item found
            for i in range(0,len(templatelist)-1):

                pos = templatelist[i].find(SERVERTYPE_KEY)
                if pos != -1:
                    optionfound = True
                    pos = pos + len(SERVERTYPE_KEY)
                    servertype = templatelist[i][pos:pos+4].strip("}").strip("{").strip("-").strip(" ")
                else:
                    servertype = None
                    
                pos = templatelist[i].find(SERVERNAME_KEY)
                if pos != -1:
                    optionfound = True
                    startpos = pos + len(SERVERNAME_KEY)
                    endpos = templatelist[i].find("--",startpos)
                    if endpos == -1:
                        endpos = len(templatelist[i])
                    servername = templatelist[i][startpos:endpos].strip("}").strip("{").strip("-").strip(" ")
                else:
                    servername = None

                pos = templatelist[i].find(SSL_KEY)
                if pos != -1:
                    optionfound = True
                    ssl = True
                else:
                    ssl = False
                                        
                pos = templatelist[i].find(USERNAME_KEY)
                if pos != -1:
                    optionfound = True
                    startpos = pos + len(USERNAME_KEY)
                    endpos = templatelist[i].find("--",startpos)
                    if endpos == -1:
                        endpos = len(templatelist[i])
                    username = templatelist[i][startpos:endpos].strip("}").strip("{").strip("-").strip(" ")
                else:
                    username = None

                pos = templatelist[i].find(PASSWORD_KEY)
                if pos != -1:
                    optionfound = True
                    startpos = pos + len(PASSWORD_KEY)
                    endpos = templatelist[i].find("--",startpos)
                    if endpos == -1:
                        endpos = len(templatelist[i])
                    password = templatelist[i][startpos:endpos].strip("}").strip("{").strip("-").strip(" ")
                else:
                    password = None

                if optionfound == True:
                    templatelist[i] = self.getOutputText(servertype,servername,ssl,username,password)
                    optionfound = False

            # go through the list concatenating the output now that it's been populated
            for item in templatelist:
                output = output + item

            return output

        #except:
            #print "getOutputTextFromTemplate:Unexpected error: ", sys.exc_info()[0]

    def getPOPEmailCount(self,servername,ssl,username,password):
        if ssl == True:
            pop = poplib.POP3_SSL(servername)
        else:
            pop = poplib.POP3(servername)            

        pop.user(username)
        pop.pass_(password)
        
        # get uid list of messages on server
        #uidlist = []
        #response, list, uid = pop.uidl()
        #for item in list:
        #    uidlist.append(item.split()[1])

        count, size = pop.stat() #get first in sequence - message count
        pop.quit()
        
        return str(count)
    
    
    def getIMAPEmailCount(self,servername,ssl,username,password):
        if ssl == True:
            imap = imaplib.IMAP4_SSL(servername)
        else:
            imap = imaplib.IMAP4(servername)
            
        imap.login(username, password)
        #typ, data = imap.select('Inbox',True)
        #count = str(len(data))

        imap.select()
        typ, data = imap.search(None, 'RECENT')    
        count = str(len(data))
           
        #for num in data[0].split():
        #    typ, data = imap.fetch(num, '(RFC822)')
        #    print 'Message %s\n%s\n' % (num, data[0][1])
        #    count = count + 1
                    
        imap.close()
        imap.logout()
        imap.shutdown()

        return str(count)

    def outputData(self):
        #try:

            if self.options.template != None:

                output = self.getOutputTextFromTemplate(self.options.template)

            else:

                output = self.getOutputText(self.options.servertype,self.options.servername,self.options.ssl,self.options.username,self.options.password)

            print output.encode("utf-8")
            
if __name__ == "__main__":

    parser = CommandLineParser()
    (options, args) = parser.parse_args()

    if options.verbose == True:
        print >> sys.stdout, "servertype:",options.servertype
        print >> sys.stdout, "servername:",options.servername
        print >> sys.stdout, "ssl:",options.ssl
        print >> sys.stdout, "username:",options.username
        print >> sys.stdout, "password:",options.password
        print >> sys.stdout, "verbose:",options.verbose

    # create new global weather object
    email = CheckEmail(options)
    email.outputData()
```

**Asique ahora tenes 7 archivos:**

En la carpeta: ~
--> .startconky <<-- hágalo ejecutable

En la carpeta: ~/Conky
--> conkymain
--> conkyforecast
--> conkyemail

y en la carpeta: ~/Conky/scripts
--> conkyForecast.py <<-- hágalo ejecutable
--> myweather.template

y en la carpeta: ~/Conky/scripts/mail
conkyEmail.py <<-- hágalo ejecutable

Yo creo que eso es todo.
Si tienes mas preguntas, pregunta nomas..

Bruce

PD:
- conkyForecast.py and conkyEmail.py fueron escritos por: [kaivalagi]("http://ubuntuforums.org/showthread.php?t=760527")
- esta informacion es traida por todas las personas que me ayudaron a configurar mi conky. Sino fuese por ellos, yo no podria haber respondido tu pedido.
- y castellano por tzulberti aquí: [dos conkys]("http://ubuntuforums.org/showthread.php?t=694880&highlight=Dos+conkys")

---

### Post by lega on 2008-05-29
muchas gracias por la ayuda, lo configure pero al iniciar me sale la captura que adjunto, el mail me da error supongo que es porque uso gmail, lo sigo viendo,y aviso gracias.

---

### Post by Bruce M. on 2008-05-29
Hola lega,

> **lega said:**
> muchas gracias por la ayuda, lo configure pero al iniciar me sale la captura que adjunto, el mail me da error supongo que es porque uso gmail, lo sigo viendo,y aviso gracias.

No pienso que trabaja con el gmail todavía. Es el primer programa y no ha habido ninguna actualizaciones todavía. El escritor está en Escocia que mira los juegos de rugbi. Los Pumas perdidos a Fiji el fin de semana pasado 17 - 21, y yo son el ventilador de los pumas. (la cresta en mi avatar)

**NO!** No soy "*el ventilador de los pumas*", soy un "fan" de Los Pumas. :lolflag:

[BabelFish]("http://ca.babelfish.yahoo.com/translate_txt") hace errores divertidos a veces.

Para ahora cambie su ~/.startconky a esto:
```
#!/bin/bash
sleep 0 & # 0 good for Xfce - use 20 to 30 for Gnome
conky -c ~/Conky/conkymain &
#sleep 0 & # 0 good for Xfce - use 1 for Gnome
conky -c ~/Conky/conkyforecast &
#sleep 0 & # 0 good for Xfce - use 1 for Gnome
#conky -c ~/Conky/conkyemail &
```

Hablaré con el escritor la semana próxima y veré si él puede agregar gmail.

Hay algo más que usted puede hacer. Agregue los alias a su archivo de /.bashrc:

```
# my aliases
alias conke='(gedit ~/.startconky ~/Conky/conkymain ~/Conky/conkyforecast ~/Conky/conkyemail ~/Conky/scripts/conkyForecast.py ~/Conky/scripts/myweather.template ~/Conky/scripts/mail/conkyEmail.py &)'
alias cia='killall conky && ./.startconky'
alias killc='killall conky'
alias stc='~/.startconky'
```

Ahora en una consola:
```
bruloo@bruloo:~$ conke
bruloo@bruloo:~$ 
```
Gedit abrirá TODOS los archivos relacionados de conky para corregir.
```
bruloo@bruloo:~$ cia
bruloo@bruloo:~$ 
```
parará conky y el comienzo conky otra vez después de realizar cambios.
```
bruloo@bruloo:~$ killc
bruloo@bruloo:~$ 
```
parará conky, él no lo comenzará otra vez.
```
bruloo@bruloo:~$ stc
bruloo@bruloo:~$ 
```
comenzará conky si no está funcionando.

Have a nice day.
(¿Tenga un día agradable? o ¿Que tenga un buen día?)
o Que tengas un buen día.
Bruce

---

### Post by lega on 2008-05-29
gracias, esta noche lo pruebo, el gmail por ahora no me interesa tanto, con esto que me dices que haga, van a quedar los dos conky por abajo de las ventanas y no me va a salir el tercero que figura en la captura?
Saludos y gracias por todo

---

### Post by Bruce M. on 2008-05-29
> **lega said:**
> gracias, esta noche lo pruebo, el gmail por ahora no me interesa tanto, con esto que me dices que haga, van a quedar los dos conky por abajo de las ventanas y no me va a salir el tercero que figura en la captura?
Saludos y gracias por todo

Correcto, habrá funcionamiento de solamente dos conkys. El que está a la derecha y la izquierda. El gmail conky no funcionará. Para comenzarlo otra vez para quitar #

Saludos,
Bruce

---

### Post by SLA_leandrin on 2008-05-29
Muy bueno.

Lo único que no me ha salido es que dibuje los íconos de nublado, o soleado o lo que corresponda, ni la flecha del viento... porque puede ser??

---

### Post by lega on 2008-05-29
en el primer mensaje estan posteados los links a las  fuentes , bajalos y copialas en usr/share/fonts, yo hice aí y anduvo
saludos

---

### Post by lega on 2008-05-30
Hola hice lo que me dijiste, ahora solo arrancan dos conky,eso se solucionó, pero sigo teniendo el problema de la captura que puse en el mensaje anterior y es que conky aparece por encima de todas las ventanas, esto pasa solo cuando inicio la pc, si yo mato el proceso con killall conky y vuelvo a arrancarlo con ./.startconky entonces si conky (ambos) quedan por debajo de toda ventana.

Por si sirve de dato tengo activado los efectos de Compiz Fusion.

Muchas gracias por la paciencia y la ayuda.:)

Saludos

---

### Post by Bruce M. on 2008-05-30
> **lega said:**
> Por si sirve de dato tengo activado los efectos de Compiz Fusion.

Muchas gracias por la paciencia y la ayuda.:)

Saludos

Hola Lega,

No tengo ninguna experiencia con Compiz. Usted necesita quizá aumentar el " sleep" tiempo en: ~/.startconky
```
#!/bin/bash
sleep 30 & # 0 good for Xfce - use 20 to 30 for Gnome
conky -c ~/Conky/conkymain &
#sleep 1 & # 0 good for Xfce - use 1 for Gnome
conky -c ~/Conky/conkyforecast &
#sleep 1 & # 0 good for Xfce - use 1 for Gnome
conky -c ~/Conky/conkyemail &
```


Pruebe esto y déjeme saber.
Mientras que buscaré una respuesta para ver si hay un problema con conky y Compiz.

Have a nice day. (Saludos)
Bruce

---

### Post by Bruce M. on 2008-05-30
> **lega said:**
> Por si sirve de dato tengo activado los efectos de Compiz Fusion.

Hola lega,

Veo otra cosa que usted puede intentar:
```
gksu gedit /etc/X11/xorg.conf
```
Si no existe, agregue la sección:
```
Section "Module"
	Load		"dbe"
EndSection
```
termine con la línea:
```
	Load		"dbe"
```
si existe esa sección agregue la línea:
```
	Load		"dbe"
```

Usted puede también intentar esto en ~/.startconky:
```
#!/bin/bash
sleep 30 & # 0 good for Xfce - use 20 to 30 for Gnome
conky -c ~/Conky/conkymain &&
#sleep 1 & # 0 good for Xfce - use 1 for Gnome
conky -c ~/Conky/conkyforecast &&
#sleep 1 & # 0 good for Xfce - use 1 for Gnome
conky -c ~/Conky/conkyemail &
```
con el doble; &&. Recuerdo usar eso con GNOME.

Saludos
Bruce

---

### Post by lega on 2008-06-01
Bruce, disclupa la demora en contestar, no había tenido tiempo de probarlo,gracias por la ayuda, pero sigue todo igual, lo que voy a hacer es sacarlo del inicio de sesion y ejecutarlo una vez que arranque todo ya que ahi si se ve bien.
Gracias nuevamente, saludos


EDITO:

Bruce, ahí funcionó! lo que hice fue anular una línea tanto en conkymain, como en conkyforecast y ahora si carga bien :), la linea es la siguiente
> 
background no
own_window yes
**#own_window_type override**

Una vez más te agradezco toda la paciencia y la predisposición para ayudarme, muchisimas gracias!
Saludos

Pd: si te enteras que el mail funciona con gmail no dejes de avisarme

---

### Post by Bruce M. on 2008-06-01
> **lega said:**
> Pd: si te enteras que el mail funciona con gmail no dejes de avisarme

Por supuesto.

Me encantó tu "wallpaper"

Saludos
Bruce

---

### Post by Bruce M. on 2008-06-01
> **lega said:**
> Pd: si te enteras que el mail funciona con gmail no dejes de avisarme

Éstos hablan de una escritura para el gmail:

[HOWTO: GMail notify with Conky]("http://ubuntuforums.org/showthread.php?t=631157")

[Re: Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showpost.php?p=2944560&postcount=312") - Éste tiene un ejemplo de funcionamiento.

[La escritura original de gmail.py]("http://www.holovaty.com/code/gmail.py")

Todos están en inglés, si usted necesita ayuda, dígame.

Usted tiene dos opciones:
[LIST=1]
[*]Espere y vea qué sucede la semana próxima con la escritura que tenemos; o
[*]Intento uno de éstos arriba.
[/LIST]

Saludos
Bruce

---

### Post by lega on 2008-06-02
Gracias bruce, probé con el primer link y funcionó perfecto, muchas gracias nuevamente:)

Saludos

---

### Post by Bruce M. on 2008-06-02
> **lega said:**
> Gracias bruce, probé con el primer link y funcionó perfecto, muchas gracias nuevamente:)

Saludos

De nada y suerte
Bruce

---

### Post by lega on 2008-06-03
Bruce no se si todavía andaras por aqui pero desde ayer dejo de salir el dibujo de la luna, si ejecuto conky desde el terminal me dice lo siguiente
> File "/home/leonardo/Conky/scripts/conkyForecast.py", line 1295, in <module>
    weather.outputData()
  File "/home/leonardo/Conky/scripts/conkyForecast.py", line 1268, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/leonardo/Conky/scripts/conkyForecast.py", line 726, in getOutputText
    output = WeatherText.conditions_moon_font[self.current_conditions[0].moon_icon]							
KeyError: u'29'



lo unico que hice fue modificar el script del mail para que lea gmail, pero nada mas, alguna idea?
saludos

---

### Post by Bruce M. on 2008-06-03
> **lega said:**
> Bruce no se si todavía andaras por aqui pero desde ayer dejo de salir el dibujo de la luna, si ejecuto conky desde el terminal me dice lo siguiente


lo unico que hice fue modificar el script del mail para que lea gmail, pero nada mas, alguna idea?
saludos

Cada uno está teniendo el mismo problema. Estamos trabajando en él.

He estado probando desde ayer.
Vea las imágenes.

Cuando es fijo cargaré el nuevo archivo de conkyForecast.py

Have a nice day.
Bruce

---

### Post by Bruce M. on 2008-06-04
Hola gente

Hay un nuevo archivo actualizado de conkyForecast.py disponible en el [Poste #6]("http://ubuntuforums.org/showpost.php?p=5063066&postcount=6")

Have a nice day
Bruce

---

### Post by santiagoward2000 on 2008-06-04
Hola Bruce!
MUY BUENO!! :)
Tengo una duda: si quiero que el CC aparezca en inglés, ¿como hago?
Saludos!

_EDIT:_
Ah! Ya lo encontré! :D No te preocupes!

---

### Post by Bruce M. on 2008-06-04
> **santiagoward2000 said:**
> Hola Bruce!
MUY BUENO!! :)
Tengo una duda: si quiero que el CC aparezca en inglés, ¿como hago?
Saludos!

_EDIT:_
Ah! Ya lo encontré! :D No te preocupes!

Vos estas rápido, también está en francés.

---

### Post by Bruce M. on 2008-11-01
Hola,

Ahora hay algo nuevo con conkyForcast. Si podes leer en ingles ver [Conky Weather Forecast Python Script]("http://ubuntuforums.org/showthread.php?t=869328"). Todos de los scripts de  kaivalagi estan en los "repos" ahora y podes usar "Synaptic" para instalarlos.

Por exemplo:

estas tres líneas, con 4 **execi**:
```
${color4}${font ConkyWeather:size=55}{execi 900 python ~/Conky/scripts/conkyForecast.py --datatype=WF}$font$color
${voffset -70}${goto 90}${color7}${font Zekton:size=20}{execi 900 python ~/Conky/scripts/conkyForecast.py --datatype=DW --shortweekday --startday=0}:$color {execi 900 python ~/Conky/scripts/conkyForecast.py --datatype=HT}
${goto 90}${voffset -10}${font Zekton:size=9}${color7}Sensación térmica: ${color}{execi 900 python ~/Conky/scripts/conkyForecast.py --datatype=LT}$font
```

podes cambiar a un **execpi**:
```
${execpi 900 conkyForecast --location=ARBA0009 --template=/home/bruloo/Conky/scripts/myweather.template}
```
**NOTA:** **execi** hasta **execpi**
y en un "template" (ie: myweather.template)

```
${color4}${font ConkyWeather:size=55}[--datatype=WF]$font$color
${voffset -70}${goto 90}${color7}${font Zekton:size=20}[--datatype=DW --shortweekday --startday=0]:$color [--datatype=HT]
${goto 90}${voffset -10}${font Zekton:size=9}${color7}Sensación térmica: ${color}[--datatype=LT]$font
${goto 15}${voffset 15}${font Zekton:size=10} ${color7}[--datatype=CC]$color$font

```
NOTA: conky puede leer los codigos normales de **${}** y conkyForcast los **[]** en el "template".

Ahora, mi **conkyforcast**
```
background no
own_window yes
own_window_type override # normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager # undecorated,below,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font DejaVu Sans Mono:size=9
xftfont DejaVu Sans Mono:size=9
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades no  # shadecolor black
default_color white
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 salmon
color6 red
color7 lightblue
color8 yellow
color9 red
alignment br  # Aligned position on screen: tl, tr, tm, bl, br, bm, ml, mr
gap_x -15
gap_y -25 # because of the VOFFSET to get the weather font up to the 2nd day, the negative "gap_y" value brings conky back to the bottom of the screen.
text_buffer_size 6076 # large buffer needed
no_buffers yes  # Subtract file system buffers from used memory?
short_units yes
pad_percents 2

TEXT
${execpi 900 conkyForecast --location=ARBA0009 --template=/home/bruloo/Conky/scripts/myweather.template}
```
y **myweather.template**
```
${color4}${font ConkyWeather:size=55}[--datatype=WF]$font$color
${voffset -70}${goto 90}${color7}${font Zekton:size=20}[--datatype=DW --shortweekday --startday=0]:$color [--datatype=HT]
${goto 90}${voffset -10}${font Zekton:size=9}${color7}Sensación térmica: ${color}[--datatype=LT]$font
${goto 15}${voffset 15}${font Zekton:size=10} ${color7}[--datatype=CC]$color$font
${goto 15}${voffset 5}${font ConkyWindN:size=40}${color4}[--datatype=BS]$font
${goto 70}${voffset -45}${color7}Viento: ${color3}[--datatype=WS] ${color7}(${color4}[--datatype=WA]°${color7}) ${color3}[--datatype=WD]
${voffset 5}${goto 70}${color7}Visibilidad:${color3} [--datatype=VI]

${color7}Presión: ${color3}[--datatype=BR] - [--datatype=BD]$color
${color7}Humedad: ${color3}[--datatype=HM]${goto 140}${color7}Precipitación: ${color3}[--datatype=PC]$color
${color7}UV: ${color3}[--datatype=UI] - ${color3}[--datatype=UT]${goto 140}${color7}P. de R.: ${color3}[--datatype=DP]$color$font
${color0}${goto 130}--------------------$color
${goto 130}${color7}[--datatype=DW --shortweekday --startday=1]:${color4}[--datatype=HT --hideunits --hidedegreesymbol --startday=1]/[--datatype=LT --hideunits --hidedegreesymbol --startday=1]${goto 210}${color7}[--datatype=DW --shortweekday --startday=2]:${color4}[--datatype=HT --hideunits --hidedegreesymbol --startday=2]/[--datatype=LT --hideunits --hidedegreesymbol --startday=2]
	${goto 30}${voffset -15}${color3}${font SunNMoon:size=50}n$font$color		${voffset -25}${color3}${font ConkyWeather:size=30}${goto 138}[--datatype=WF --startday=1]${goto 218}[--datatype=WF --startday=2]$font
	${goto 30}${voffset 5}${color0}${font Arrows:size 20}b$font${color3}[--datatype=SR]${goto 130}${color7}Sol:${color4}[--datatype=SR --startday=1]${goto 210}${color7}Sol:${color4}[--datatype=SR --startday=2]
	${goto 30}${color7}Luz:${color3}[--datatype=DL]${goto 130}${color7}   :${color4}[--datatype=SS --startday=1]${goto 210}${color7}   :${color4}[--datatype=SS --startday=2]  
	${goto 30}${color0}${font Arrows:size 20}h$font${color3}[--datatype=SS]${goto 130}${color7}Luz:${color4}[--datatype=DL --startday=1]${goto 210}${color7}Luz:${color4}[--datatype=DL --startday=2]
${color0}${goto 130}--------------------$color
${goto 130}${color7}[--datatype=DW --shortweekday --startday=3]:${color4}[--datatype=HT --hideunits --hidedegreesymbol --startday=3]/[--datatype=LT --hideunits --hidedegreesymbol --startday=3]${goto 210}${color7}[--datatype=DW --shortweekday --startday=4]:${color4}[--datatype=HT --hideunits --hidedegreesymbol --startday=4]/[--datatype=LT --hideunits --hidedegreesymbol --startday=4]
	${goto 30}${color4}${font moon phases:size=50}[--datatype=MF]$font	${voffset -46}${color3}${font ConkyWeather:size=30}${goto 135}[--datatype=WF --startday=3]${goto 215}[--datatype=WF --startday=4]$font$color
${goto 130}${color7}Sol:${color4}[--datatype=SR --startday=3]${goto 210}${color7}Sol:${color4}[--datatype=SR --startday=4]
${goto 130}${color7}   :${color4}[--datatype=SS --startday=3]${goto 210}${color7}   :${color4}[--datatype=SS --startday=4]  
${goto 130}${color7}Luz:${color4}[--datatype=DL --startday=3]${goto 210}${color7}Luz:${color4}[--datatype=DL --startday=4]
${font DejaVu Sans Mono:size=7}${alignc 0}W:[--location=ARBA0009 --datatype=LU] -=- C:[--location=ARBA0009 --datatype=LF]
```
Solo un **execpi**, y tengo todo en mi pantalla - ver la imagen:

---

### Post by josedb on 2008-11-01
Cuando quiero ejecutar, o bien tu script, o el ejemplo que viene con el conkyweather me sale esto....



> jose@jose-laptop:~$ conky -c style/conkyweather
Conky: desktop window (20000a3) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (0x4200001)
Conky: drawing to double buffer
ERROR: Config data file /home/jose/.conkyForecast.config not found, using defaults (Registration info is needed though)
Traceback (most recent call last):
  File "/usr/share/conkyforecast/conkyForecast.py", line 1302, in <module>
    weather = Weather(options)
  File "/usr/share/conkyforecast/conkyForecast.py", line 448, in __init__
    socket.setdefaulttimeout(self.config.CONNECTION_TIMEOUT)
AttributeError: 'NoneType' object has no attribute 'CONNECTION_TIMEOUT'
^CConky: received SIGINT or SIGTERM to terminate. bye!



EDITl

Bueno ahora hice un par de modificaciones en rutas, y agregue la info que faltaba en el config, el partner id, y la licencia.

pero ahora me dice esto....


> jose@jose-laptop:~$ conky -c Conky/conkyforecast 
Conky: desktop window (20000a3) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (0x4000001)
Conky: drawing to double buffer
*** buffer overflow detected ***: conky terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f8804efc887]
/lib/libc.so.6[0x7f8804efa750]
/lib/libc.so.6[0x7f8804ef996d]
conky[0x414498]
conky[0x414750]
conky[0x418479]
conky[0x419266]
conky[0x41a955]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f8804e1b466]
conky[0x405ca9]
======= Memory map: ========
00400000-00437000 r-xp 00000000 08:04 8333124                            /usr/bin/conky
00636000-00637000 r--p 00036000 08:04 8333124                            /usr/bin/conky
00637000-00638000 rw-p 00037000 08:04 8333124                            /usr/bin/conky
00638000-00646000 rw-p 00638000 00:00 0 
01e36000-01e99000 rw-p 01e36000 00:00 0                                  [heap]
7f8802a5d000-7f8802a73000 r-xp 00000000 08:04 1302589                    /lib/libgcc_s.so.1
7f8802a73000-7f8802c73000 ---p 00016000 08:04 1302589                    /lib/libgcc_s.so.1
7f8802c73000-7f8802c74000 r--p 00016000 08:04 1302589                    /lib/libgcc_s.so.1
7f8802c74000-7f8802c75000 rw-p 00017000 08:04 1302589                    /lib/libgcc_s.so.1
7f8802c75000-7f8802c9c000 r-xp 00000000 08:04 8334120                    /usr/lib/libexpat.so.1.5.2
7f8802c9c000-7f8802e9c000 ---p 00027000 08:04 8334120                    /usr/lib/libexpat.so.1.5.2
7f8802e9c000-7f8802e9e000 r--p 00027000 08:04 8334120                    /usr/lib/libexpat.so.1.5.2
7f8802e9e000-7f8802e9f000 rw-p 00029000 08:04 8334120                    /usr/lib/libexpat.so.1.5.2
7f8802e9f000-7f8802ea4000 r-xp 00000000 08:04 8333878                    /usr/lib/libXdmcp.so.6.0.0
7f8802ea4000-7f88030a3000 ---p 00005000 08:04 8333878                    /usr/lib/libXdmcp.so.6.0.0
7f88030a3000-7f88030a4000 rw-p 00004000 08:04 8333878                    /usr/lib/libXdmcp.so.6.0.0
7f88030a4000-7f88030cc000 r-xp 00000000 08:04 1302640                    /lib/libpcre.so.3.12.1
7f88030cc000-7f88032cb000 ---p 00028000 08:04 1302640                    /lib/libpcre.so.3.12.1
7f88032cb000-7f88032cc000 r--p 00027000 08:04 1302640                    /lib/libpcre.so.3.12.1
7f88032cc000-7f88032cd000 rw-p 00028000 08:04 1302640                    /lib/libpcre.so.3.12.1
7f88032cd000-7f88032d6000 r-xp 00000000 08:04 8333904                    /usr/lib/libXrender.so.1.3.0
7f88032d6000-7f88034d5000 ---p 00009000 08:04 8333904                    /usr/lib/libXrender.so.1.3.0
7f88034d5000-7f88034d6000 r--p 00008000 08:04 8333904                    /usr/lib/libXrender.so.1.3.0
7f88034d6000-7f88034d7000 rw-p 00009000 08:04 8333904                    /usr/lib/libXrender.so.1.3.0
7f88034d7000-7f8803555000 r-xp 00000000 08:04 8334138                    /usr/lib/libfreetype.so.6.3.18
7f8803555000-7f8803755000 ---p 0007e000 08:04 8334138                    /usr/lib/libfreetype.so.6.3.18
7f8803755000-7f880375a000 r--p 0007e000 08:04 8334138                    /usr/lib/libfreetype.so.6.3.18
7f880375a000-7f880375b000 rw-p 00083000 08:04 8334138                    /usr/lib/libfreetype.so.6.3.18
7f880375b000-7f880378b000 r-xp 00000000 08:04 8334130                    /usr/lib/libfontconfig.so.1.3.0
7f880378b000-7f880398b000 ---p 00030000 08:04 8334130                    /usr/lib/libfontconfig.so.1.3.0
7f880398b000-7f880398c000 r--p 00030000 08:04 8334130                    /usr/lib/libfontconfig.so.1.3.0
7f880398c000-7f880398d000 rw-p 00031000 08:04 8334130                    /usr/lib/libfontconfig.so.1.3.0
7f880398d000-7f880398f000 r-xp 00000000 08:04 8333867                    /usr/lib/libXau.so.6.0.0
7f880398f000-7f8803b8e000 ---p 00002000 08:04 8333867                    /usr/lib/libXau.so.6.0.0
7f8803b8e000-7f8803b8f000 rw-p 00001000 08:04 8333867                    /usr/lib/libXau.so.6.0.0
7f8803b8f000-7f8803baa000 r-xp 00000000 08:04 8334813                    /usr/lib/libxcb.so.1.0.0
7f8803baa000-7f8803da9000 ---p 0001b000 08:04 8334813                    /usr/lib/libxcb.so.1.0.0
7f8803da9000-7f8803daa000 r--p 0001a000 08:04 8334813                    /usr/lib/libxcb.so.1.0.0
7f8803daa000-7f8803dab000 rw-p 0001b000 08:04 8334813Cancelado
jose@jose-laptop:~$ 




EDIT2:

Ahora arranca, pero se ve mal :) dejo un screenshot y mi conkyrc
> background no
font Sans:size=7
xftfont Sans:size=7
#xftfont Andale Mono-9
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
#xftfont squaredance10:pixelsize=14
#xftfont swf!t_v02:pixelsize=10
use_xft yes
xftalpha 1
update_interval 0.5
#total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 300 5
maximum_width 250
default_color black #d7d7d7
default_shade_color black
default_outline_color red #black
alignment top_right
gap_x 2
gap_y 10
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no
override_utf8_locale yes
net_avg_samples 2
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 white
color6 white
color7 white
color8 white
color9 white
TEXT



${voffset 6}${font arial black:size=30}${time %e}$font ${voffset -17}${time %A, }${time %B} ${time %G}
${voffset -2}${goto 65}${font arial black:size=10} ${time %I:%M:%S %p} $font
Uptime:$uptime

$color4 Batt:$color ${battery} $alignc ${color #E1D93F}${battery_bar 8} $color

SYSTEM ${hr 1 }
Hostname: $alignr$nodename
Kernel: $alignr$kernel
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

CPU 1  ${execi 30 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor}    ${alignc} ${freq}MHz / ${hwmon 0 temp 1 input}C ${alignr}(${cpu cpu1}%)
CPU 2  ${execi 30 cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor}    ${alignc} ${freq}MHz / ${hwmon 0 temp 3 input}C ${alignr}(${cpu cpu2}%)
${cpugraph}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}

FILESYSTEM ${hr 1}${color}
Root: ${fs_free_perc /}% ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}

NETWORK ${hr 1}${color}
IP Addres: ${addr eth0} ${alignr}External:$font${execi 14400 wget -O - [http://whatismyip.org/](http://whatismyip.org/) | tail}
IP Addres: ${addr ath0}                 
                                      Ethernet
Down ${color green}${downspeed eth0} $color k/s ${alignr}Up ${color red}${upspeed eth0} $color k/s
${downspeedgraph eth0 25,107} ${alignr}${upspeedgraph eth0 25,107}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

                                        Wlan
Down ${color green}${downspeed ath0} $color k/s ${alignr}Up ${color red}${upspeed ath0}$color k/s
${downspeedgraph ath0 25,107} ${alignr}${upspeedgraph ath0 25,107}
Total ${totaldown ath0} ${alignr}Total ${totalup ath0}


${execpi 900 conkyForecast --location=ARBA0009 --template=/home/jose/Conky/scripts/myweather.template}



[[IMG]http://img60.imageshack.us/img60/4580/pantallazotu3.png[/IMG]](http://imageshack.us)
[[IMG]http://img60.imageshack.us/img60/pantallazotu3.png/1/w1280.png[/IMG]](http://g.imageshack.us/img60/pantallazotu3.png/1/)

---

### Post by Bruce M. on 2008-11-01
¿Tenes tu propio **Partner ID** & **License Key** por email de [weather.com]("http://www.weather.com/services/xmloap.html") como este?

```
2008/10/29 <admin@talk2.weather.com>

    Dear xxxxxxxxx@gmail.com,

    Thank you for registering for the weather.com XML Data Feed (the "Service"). Please print or save this e-mail message for future reference.

    IMPORTANT INFORMATION CONCERNING ACCESS TO THE weather.com XML Data Feed IS ENCLOSED.

    The Service allows third-party Internet web sites (non-Mobile Web sites) and desktop applications to access a subset of the data available on www.weather.com via an on-request XML feed. The Weather Channel Interactive, Inc. (TWCi) provides this data free of charge to partners who wish to incorporate weather into their single Internet web site or single Desktop Application in exchange for five (5) promotional links, including an embedded link within the TWCi Logo, back to www.weather.com. These Required Links are specified by TWCi in the Service on each data request and are returned via the "&link=xoap" parameter of the Service. The Required Links must be displayed in close proximity to the TWCi Content.

    This e-mail summarizes some of the key points that you have already agreed to in the License Agreement for the Service. The complete terms and conditions surrounding the use of the Service can be found in the developer sdk along with graphical icons that are necessary to represent the sky conditions associated with our current conditions and forecast data, and our logo. This sdk can be accessed by clicking on the link below.

    http://download.weather.com/web/xml/sdk.zip

    You may update your user profile or change your product selections at any time by logging in to the weather.com registration system with the following information:

    Sign-In Page: https://registration.weather.com/ursa/xmloap/step1
    E-mail address: b1canuck@gmail.com

    VERY IMPORTANT:

    YOU MAY NOT USE THE SERVICE TO CREATE WEATHER AND WEATHER-RELATED PRODUCTS TO BE DISPLAYED ON HANDHELD OR OTHER WIRELESS DEVICES.

    YOU MAY NOT USE THE SERVICE IN CONNECTION WITH AMONG OTHER THINGS, ANY BROADCAST TELEVISION, INTERACTIVE TELEVISION, CABLE TELEVISION, TELEPHONE OR DSL SERVICES, DIGITAL CABLE SERVICES, HEAD-END-IN-THE-SKY SATELLITE SYSTEMS, RADIO, PRINT PUBLICATIONS, DIGITAL BROADCAST SATELLITES, TELEMATICS, TELETEXT, VIDEO-ON-DEMAND, KIOSKI DISPLAY, OR OTHER PUBLIC OR PRIVATE INFORMATION DISPLAY UNIT, WIRE-LINE TELEPHONE, OR AS ALL OR PART OF ANY STREAMING VIDEO OR AUDIO CONTENT OR FOR DELIVERY BY ANY MEANS OTHER THAN STATIC DISPLAY ON A TRADITIONAL WEB PAGE ON YOUR WEBSITE OR DESKTOP APPLICATION.

    YOU MAY NOT USE ANY LATITUDE OR LONGITUDE DATA ASSOCIATED WITH A LocID EVEN IF SUCH INFORMATION IS RETURNED AS PART OF AN XML DOCUMENT FROM THE XML FEED.

    USE OF THE SERVICE IN VIOLATION OF THE TERMS OF YOUR AGREEMENT WITH TWCi MAY RESULT IN YOUR IMMEDIATE TERMINATION AND PAYMENT OF MONETARY DAMAGES TO TWCi.

    The Service includes:

        * city search capability for all locations covered by www.weather.com;
        * location specific information necessary for data presentation;
        * current condition information (Observations) for the selected location; and
        * up to five (5) days of forecast information (the current day's forecast plus four additional days of forecast information in consecutive order beginning with tomorrow's forecast) for the selected location in ten (10), 12-hour day-parts.

    To comply with the terms of the Agreement, Your Website or Desktop Application must, among other things:

        * display weather data for no more than three (3) locations at a time;
        * adhere to the data request rules, usage rules, and refresh rates outlined in Exhibit B of the Agreement;
        * clearly separate TWCi data from other data within a single visual element;
        * identify that the weather data comes from TWCi by incorporating The Weather Channel logo containing an embedded link to the www.weather.com home page (one of 5 Required Links);
        * provide four (4) promotional links, selected by TWCi and provided through the Service on each data call, back to www.weather.com for additional weather information in close proximity to the TWCi Content as set forth in Exhibit B of the Agreement; and
        * be free of charge to your end-users.


    If you cannot meet these requirements but would still like to use our weather data, please contact our business development department at 770-226-0000.

    Your weather.com XML Partner ID & License Key:

    **Partner ID: ###########**
    **License Key: ############**

    Properly Formatted XML Request for the Service:

    Example: a properly formatted request for Current Conditions and a Five-Day forecast for Atlanta, Georgia from the Service will appear as follows:

    http://xoap.weather.com/weather/local/30339?cc=*&dayf=5&link=xoap&prod=xoap&par=[PartnerID]&key=[LicenseKey]

    where [PartnerID] is your unique Partner ID and [LicenseKey] is your unique License Key.

    If you have any questions about the Service, please contact us at:

    http://www.weather.com/interact/contactus/XOAPfeedback.html
    or call our business development team at 770-226-0000, Monday - Friday, 9:30 am EDT/EST - 5:00 p.m. EDT/EST, excluding Holidays.

    Regards,

    From your friends at
    The Weather Channel Interactive, Inc
    (a/k/a weather.com)

    P.S. - If you did not register for a product or service on weather.com or if you received this message in error, you can automatically deactivate the account now by visiting: https://registration.weather.com/ursa/profile

```
Necesitas introducirlos en **conkyForecast.config**.

Chimo!
Bruce

---

### Post by josedb on 2008-11-01
Bueno, parece que ya no voy a molestar a nadie.

les dejo el screen de como quedo... si alguno tiene una sugerencia para mejorarlo sera bienvenido

[[IMG]http://img521.imageshack.us/img521/2935/pantallazoor9.th.png[/IMG]](http://img521.imageshack.us/my.php?image=pantallazoor9.png)[[IMG]http://img521.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

