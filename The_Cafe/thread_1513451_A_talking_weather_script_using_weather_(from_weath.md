---
title: "A talking weather script using weather (from weather-util)"
date: 2010-06-19
forum: The Cafe
---

### Post by GraysonPeddie on 2010-06-19
Hi everyone. I'd like to contribute my script to everyone who want to use it in Linux. You'll need weather-util and a choice of either espeak or festival (change the OUTPUT to the one you use).

I've tested my script and it should work for yours. Just change the information about which airport you are located close to and be sure you edit /etc/weatherrc and get the 4-letter identifier in weather.noaa.gov.

Well, here you go.

```
#!/bin/bash
# Speak out to the user telling that you want to give the user
# a weather report.

# Change this to your preferences (such as /usr/bin/festival).
OUTPUT="/usr/bin/padsp /usr/bin/espeak -ven+m3 -a 125 -p 40 -s 140"

$OUTPUT "Hello. This is e-Speak speech synthesizer in Ubuntu Server 10.04."

OUTPUT="/usr/bin/padsp /usr/bin/espeak -ven+m3 -a 125 -p 25 -s 160"

# Pause for 1 second.
sleep 1

$OUTPUT "I would like to give you the weather information that is close to Orlando International Airport. Please hold on for a second."

OUTPUT="/usr/bin/padsp /usr/bin/espeak -ven+m3 -a 125 -p 32 -s 120"

# Three seconds.
sleep 3

# This temporary file will be the basis for the entire script.
TEMPFILE=/tmp/weather.txt

# Copy the weather information you get from the Internet into the temp file.
/usr/bin/weather > $TEMPFILE
# Get the temperature.
TEMP=$(awk '/Temperature/ {print $2}' $TEMPFILE)
TEMP="The temperature is: $TEMP degrees "

# Get the information for the sky.
SC=$(cat $TEMPFILE | grep "Sky conditions: " | sed -e 's/Sky conditions: //g')
SC="with $SC skies. "

# Get the information for the weather.
WC=$(cat $TEMPFILE | grep 'Weather: ' | sed -e 's/Weather: //g' -e 's/ observed//g')
# This is to make it clear for the user when it comes to details about the
# weather. Sed (stream editor) replaces the semi-colons and commas depending
# on how much information there are.
if [[ $WC == *,* ]]
then
    WC=$(echo $WC | sed -e 's/,/, and/g')
    WC=$(echo $WC | sed -e 's/;/,/g')
else
    WC=$(echo $WC | sed -e 's/;/ and/g')
fi

# If there are any weather conditions, then let WC know so it can be processed
# to the output depending in which engine is used.
if [ "$WC" != "" ]
then
    WC="The weather condition is: $WC. "
fi

# Get the wind condition.
WIND=$(cat $TEMPFILE | grep 'Wind: ')

# You may not get the direction and the speed of the wind if it's calm,
# so make it clear to the user.
if [[ "$WIND" == *Calm* ]]
then
    WIND="The wind is calm at this time. "
else # Get the wind direction and speed.
    # Get the direction of the wind. The degree of an angle is not very
    # meaningful to the user.
    WINDDIR=$(awk '/Wind: / {print $4}' $TEMPFILE)
    # Translate the abbreviations (N, NE, E, etc.) so that the user can
    # understand.
    case $WINDDIR in
        N)
            WINDDIR="north"
            ;;  # This ";;" is similar to that of a "break statement" for
                # those who know C/C++/C#.
        NNE)
            WINDDIR="north-northeast"
            ;;
        NE)
            WINDDIR="northeast"
            ;;
        ENE)
            WINDDIR="east-northeast"
            ;;
        E)
            WINDDIR="east"
            ;;
        ESE)
            WINDDIR="east-southeast"
            ;;
        SE)
            WINDDIR="southeast"
            ;;
        SSE)
            WINDDIR="south-southeast"
            ;;
        S)
            WINDDIR="south"
            ;;
        SSW)
            WINDDIR="south-southwest"
            ;;
        SW)
            WINDDIR="southwest"
            ;;
        WSW)
            WINDDIR="west-southwest"
            ;;
        W)
            WINDDIR="west"
            ;;
        WNW)
            WINDDIR="west-northwest"
            ;;
        NW)
            WINDDIR="northwest"
            ;;
        NNW)
            WINDDIR="north-northwest"
            ;;
    esac
    # Get the wind speed.
    WINDSPEED=$(awk '/Wind: / {print $8,"miles per hour"}' $TEMPFILE)

    # Make it clear to the user about the wind direction and speed.
    WIND="The direction of the wind is from: $WINDDIR at $WINDSPEED. "
fi

# Get the amount of rain in inches during the last hour.
PRECIPINCHES=$(awk '/Precipitation last hour: / { print $4}' $TEMPFILE)
if [ "$PRECIPINCHES" != "" ]
then
    PRECIPINCHES="The amount of rain during the last hour is: $PRECIPINCHES and the "
else
    PRECIPINCHES="The "
fi

# Get the relative humidity.
HUMIDITY=$(awk '/Relative Humidity/ {print "relative humidity is at",$3}' $TEMPFILE)

# Last, but not least, output all the current weather information to the
# engine that is currently set in the "OUTPUT" setting.
$OUTPUT "$TEMP$SC$WC$WIND$PRECIPINCHES$HUMIDITY"

# Give it a one-second pause.
sleep 1

# Now get the weather forcast from the temporary file.
FORECAST=$(cat $TEMPFILE | sed -n '/Sky conditions:/,$ p' | sed -n '2,$ p')

# Please change the word "precipitation" to "rain."
FORECAST=$(echo $FORECAST | sed 's/precipitation/rain/g')

# Output to the user the weather forecast.
$OUTPUT "Here's your local forecast: $FORECAST"

# Go ahead and pause for a second.
sleep 1

# Now go ahead and finish off to complete the weather report for the user.
case $(date +%A) in # "A" gives the output of the full name of the day.
    Sunday)
        $OUTPUT "Have a good sunny day!"
        ;;
    Monday)
        $OUTPUT "Start your day off by having some nice cup of sweet hot tea before you leave for work or class and have a good day."
        ;;
    Tuesday)
        $OUTPUT "Have a good day!"
        ;;
    Wednesday)
        $OUTPUT "This week is halfway over, but don't rush yourself during the day and for the rest of the week. Have a nice day."
        ;;
    Thursday)
        $OUTPUT "Have a nice and beautiful day."
        ;;
    Friday)
        $OUTPUT "Make a big smile in your face as this is the last working day of the week. Have a good one and see you back tonight."
        ;;
    Saturday)
        $OUTPUT "Have a nice and beautiful day."
        ;;
esac

# Clean up.
rm $TEMPFILE

# End the bash script with a success!
exit 0
```

Put that script in the directory you like, put the path of script in a crontab, set it to 7 AM, and away you go! :)

If you have some improvements you that you want to make for this script, please let me know.

Here's mine (I have some other things, too):

```
0 7 * * * /usr/bin/espeak "Good morning!"
1 7 * * * /usr/scripts/get_weather
0 3,5-19,22 * * * /usr/bin/espeak "The time is $(/bin/date \+\%-l) $(/bin/date \+\%p)"
0 22 * * * /usr/bin/espeak "Good night."
```

Enjoy.

Oh, by the way, with my computer doing the speaking when it comes to providing information, this reminds me of HomeSeer, since I used to do home automation. I did not purchase HomeSeer, as I couldn't afford it, but with Linux, it makes my Ubuntu Server become a part of my apartment. As you can see in the list of cron jobs, it's great to use it as a reminder to wake me up, or telling me "good night," or maybe announce the time every hour (except during nights between 10 PM to 3 AM), and it gives me a lot of flexibility.

What it could be very useful is I could setup a wireless doorbell that can trigger a relay and tell my Ubuntu server that a visitor is here. (I currently have a wireless doorbell for my apartment but lost the device that houses the button, so I'll have to get a new one.)

Ah... The beauty of Linux! :D

PS: In the future, is there a place where I can contribute my scripts for anyone to use?

PPS: I got the eSpeak working through padsp (PulseAudio in my Ubuntu Server without an X environment running) but does anyone know how I can get this to work in my script? I tried OUTPUT=/usr/bin/padsp /usr/bin/espeak instead of OUTPUT=/usr/bin/espeak but it's not working. Is there a way around it? The reason why I want this is because with the use of PulseAudio sound server, I want to distribute the sound to my netbook without adding expensive wireless speakers in my apartment.

---

### Post by sanderd17 on 2010-06-19
Great script but I did need to give and id of the weather station (an ICAO id from the list [http://aviationweather.gov/adds/metars/stations.txt]("http://aviationweather.gov/adds/metars/stations.txt")) on line 22.

For sharing your script, maybe make a little Google code project. But I'm glad you mentioned it here, otherwise I wouldn't have found it.

Maybe something else you can try: switch the bureau background to an image related to the weather (a lightning bold if it's storming, a rainy windows when it's raining, a sunny beach when it's hot ...)

If you do it, I would like to see the result.

Greets, Sander

---

### Post by GraysonPeddie on 2010-06-19
Thanks. I am using Ubuntu Server and that will require a X-Window server in order to do that (in my home theater PC).

One unrelated question: Is it possible to post my code without showing my email address (even an obscured e-mail address like yourname@... which then the e-mail address can be displayed once the user passes the easily-defeatable CAPTCHA)?

---

### Post by sanderd17 on 2010-06-19
in google code, I don't think so. But you can just make a new google account can't you?
But you should mention on the project that it isn't your real e-mail, or people would be upset they don't get an answer.

I don't mind privacy, I use the same username for the forums as my e-mail adress, my wikipedia account, my OSM work... I just try to prevent that my e-mail is readable by bots. But I think it's to late for it now since my sister filled in her hotmail pwd in an obscure site which read her address book an which already send me a mail.

If someone wants to find you, he can.

---

### Post by GraysonPeddie on 2010-06-19
Okay, thanks. I haven't got any spam recently.

---

### Post by GraysonPeddie on 2010-06-21
Hi, everyone. I've updated the script in my first post. I've customized the script to give eSpeak more variation in pitch and speech rate. Plus, I've implemented a check in $PRECIPINCHES that if the information for the amount of rain during the last hour is not available, as is the case for weather conditions, the eSpeak does not speak the portion of the sentence except to start with "The" with a capital "T." To me, I think that grammatical structure is very important for me (but may not be important for some) because when I construct a script like this, it gives a clear and concise information. However, I did implement the columns to pause the speech before speaking the temperature, weather condition, wind direction, and that's about it as far as making the weather information clearer for those who are not near their computer to get the weather information. The condition for sky and wind speed does not need a colon as the colons already provide a break before speaking out the temperature and wind direction.

Attached is a sample of what you'll hear when you hear the weather information coming through your speakers.

Now if only eSpeak could speak out to all my computer speakers regardless of operating system (Windows, Linux, etc.)...

---

