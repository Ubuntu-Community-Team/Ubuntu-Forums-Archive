---
title: "TextfileToMp3 nautilus script"
date: 2007-06-06
forum: The Cafe
---

### Post by PatrickMay16 on 2007-06-06
I've created a script for nautilus that turns a text file into an mp3 file. It's not very good, but it works, and maybe someone else would find it handy. I'd appreciate any suggestions for improvement, like making it able to handle multiple files instead of just one... I'm very poor at bash scripting.

```

## Textfile2mp3 - a simple bash script to turn a textfile into an mp3.
## By P May. COCK-BENIS.

export voice_wave_file=-$RANDOM

text2wave "$1" -o "voice$voice_wave_file.wav"

lame -v -b 8 -B 32 "voice$voice_wave_file.wav" "$1.mp3"

rm "voice$voice_wave_file.wav"

```

---

### Post by benanzo on 2007-06-06
I'm not good at BASH either, but I like to fool around.  Here's mine:

```

#!/bin/bash
##### Convert any text files to mp3s
# script to automatically convert text to mp3s and move them to iPod queue.
TXT_DIR="${HOME}/text"

cd ${TXT_DIR}
for TEXT in *.txt ; do
	/usr/bin/text2wave -scale 10 ${TEXT} -o ${TEXT}.wav
	/usr/bin/lame "${TEXT}.wav" "${TEXT}.mp3"
	/usr/bin/eyeD3 --to-v2.4 -a "${TEXT}" -A "Text File" -t "${TEXT}" "${TEXT}.mp3"
	cp "${TEXT}.mp3" ${QUEUE_DIR}
	/usr/bin/mplayer ${SUCCESS_ALERT}
	mv ${TEXT} ${TXT_DIR}/old
	rm ${TEXT}* 
done

```

This doesn't have any interactivity on the CLI.  It works by just creating a .txt file in the specified directory and pasting your text into it.  It will go through every text file in the dir and create an mp3.  Works pretty well for me.

${QUEUE_DIR} is whatever directory you want the final mp3 to go and ${SUCCESS_ALERT} is just a jingle I have it play when it's done.

eyeD3 just adds some metadata (the name of the file) to the final mp3.

---

