---
title: "Producing Dial-Tone With Mgetty"
date: 2010-10-24
forum: Server Platforms
---

### Post by TeamXlink on 2010-10-24
I'm trying to produce a dial-tone from my modem with Mgetty.

I found this online:

> I recently discovered a feature that's part of the command set of some voice modems that enables it to produce tones. The latter is of interest to us since the US dial-tone and others are a combination of two frequencies (440Hz and 350Hz in the US).

Below is an ordered list of AT commands that initialize the modem, produce a dialtone for 2.5 seconds and answers the call. To check if the "AT+VTS" command is supported, or to get the parameter value ranges supported by it, use "AT+VTS=?"


# resets the modem
ATZE1

# puts the modem into voice mode
AT+FCLASS=8

# opens the connection
AT+VLS=1

# produces the tone
AT+VTS=[440,350,255]

# closes the connection so it can answer
ATH

# answers the connection
ATA

* Usage: The first two parameters are the desired frequencies. The third parameter is the duration of the tone and is the desired time (in milliseconds) / 10. If the square brackets do not work, try using "{ }" backets as an alternative.

* Note: Some voice modems use "#" instead of the "+" character for the VLS and VTS commands. If the modem is returning "ERROR" after sending either command, try replacing the character.

I'm unsure of how to enter those commands.

My setup is:

Ubuntu 8.04 CLI Install

Thank you.

---

### Post by TeamXlink on 2010-10-29
I'm still trying to produce the dial-tone with mgetty.

This is my mgetty.config file in /etc/mgetty

```

debug 4
fax-id
speed 38400
issue-file /etc/issue.mgetty
init-chat ""

```

This is my options file in /etc/ppp


```

debug
login
require-pap
ms-dns 192.168.1.1
proxyarp
ktune

```

This is my options.ttySHSF1 in /etc/ppp

```

192.168.1.150:192.168.1.151
netmask 255.255.255.0

```

*Note: ttySHSF1 is the name of the modem I'm using

I can connect with some things, but if it requires a dial-tone, I have to do annoying, lengthy workarounds that are needed if I can do this.

```

# resets the modem
ATZE1

# puts the modem into voice mode
AT+FCLASS=8

# opens the connection
AT+VLS=1

# produces the tone
AT+VTS=[440,350,255]

# closes the connection so it can answer
ATH

# answers the connection
ATA

```

These are what I need to set my modem to do, I think it needs to be ran in a script style, executing one after another.

I don't understand how to do this, or what the syntax for multiple commands are.

I thought it might have to do with the init-chat line in mgetty.config but after looking it up online, it seems it goes in the forum of a send, confirm, send, confirm..., I think I just need to do it in a forum of send, send, send....

If I have to do it in the init-chat sequence, how to I string the modem commands together?

Do I do it like this:

```

init-chat "ATZE1&AT+FCLASS=8&AT+VLS=1&AT+VTS=[440,350,255]&ATH&ATA"

```

Or this:

```

init-chat "ATZE1;AT+FCLASS=8;AT+VLS=1;AT+VTS=[440,350,255];ATH;ATA"

```

Or this:

```

init-chat "ATZE1 ok AT+FCLASS=8 ok AT+VLS=1 ok AT+VTS=[440,350,255] okATH ok ATA"

```

Or this:

```

init-chat "ATZE1AT+FCLASS=8AT+VLS=1AT+VTS=[440,350,255]ATHATA"

```

Or some other way?

I'm very eager to get this working.

Thank you.

---

### Post by psusi on 2010-10-29
I can't make sense out of what you are trying to do.  The modem does not produce the dial tone; the telephone company does.  The modem then dials a number and begins communicating with the modem that answers the other end.

---

### Post by TeamXlink on 2010-10-29
> **psusi said:**
> I can't make sense out of what you are trying to do.  The modem does not produce the dial tone; the telephone company does.  The modem then dials a number and begins communicating with the modem that answers the other end.

I'n not using a telephone company.

The computer has an etherenet port with an ethernet cable attaching it to our router.

The computer also has a modem.

Another device I have only has a modem.

My other device is plugged into my computer modem via a telephone cord.

I call in and mgetty answers and it connects to the internet.

Some software doesn't support blind dial, meaning it has to hear a dial tone.

Right now I have to either:

A: Have a cord plugged into my telephone port to get the dial tone and quickly switch the modem cords to the one connecting it to my computer.

B: Have a phone cord that is spliced and soldered to a headphone plug that I plug into another computer to play a dial-tone sound file.

---

### Post by TeamXlink on 2010-11-01
I'm still trying to accomplish this, I think it may be my lack of a decent explanation.

I have two devices.

A PC running Linux.

And another device that only has a modem.

My PC has mgetty and ppp installed and is acting like a dial-up ISP server.

My device's has a phone cord running from my devices modem to the line in port modem on my PC.

So:

PC = Dial-Up ISP

Other Device = Device Dialing into the ISP

Other Device Requires: Dial-Tone


Or, does anyone know of a guide on how to create a Dial-UP ISP in Linux using mgetty & ppp thats detailed.

Thank you.

---

### Post by TeamXlink on 2010-11-01
> **psusi said:**
> I can't make sense out of what you are trying to do.  The modem does not produce the dial tone; the telephone company does.  The modem then dials a number and begins communicating with the modem that answers the other end.

I just read the telephone company part.

My PC *is* the telephone company. My other device is the one that dials a number and begins communicating with the modem on my PC.

---

### Post by TeamXlink on 2010-11-02
This is another bump.

I usually try and do a bump every 24 hours after the last post was made, while adding any more information that might help people know how to help me with this, but I have no information for this one.

---

### Post by TeamXlink on 2010-11-06
Bump.

---

### Post by TeamXlink on 2010-11-19
Bump.

---

### Post by TeamXlink on 2010-11-20
Bump.

---

