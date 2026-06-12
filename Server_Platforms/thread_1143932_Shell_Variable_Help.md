---
title: "Shell Variable Help"
date: 2009-04-30
forum: Server Platforms
---

### Post by etechship on 2009-04-30
I have the following command running from upload.sh

```
ffmpeg -i "$outputFile.flv" -v 0 -vn "$outputFile-a.flv"
```

The input file is read correctly, but it assumes the output is '.flv'. So how can I make the outpute, as stated above, $outputFile-a.flv.

Thanks
dave

---

### Post by FakeOutdoorsman on 2009-04-30
I don't understand your question.  What do you mean by, "it assumes the output is '.flv'"?  Also, what are you trying to do with FFmpeg?  Right now this command re-encodes the audio from the original file into a FLV container.  This isn't as efficient as just copying the audio stream:
```
ffmpeg -i input.flv -acodec copy output.mp3
```

---

### Post by etechship on 2009-05-01
I want to leave it as a flash file. I would just like the variable in the second part to work.

dave

---

### Post by koenn on 2009-05-01
Your question is rather unclear. It would help if you'd specify what exactly the variable name is. 
That's probably also the problem the shell has with your command.

assuming 'outputFile' is a variable, try
```

ffmpeg -i "${outputFile}.flv" -v 0 -vn "${outputFile}-a.flv"

```

---

### Post by FakeOutdoorsman on 2009-05-01
> **etechship said:**
> I want to leave it as a flash file. I would just like the variable in the second part to work.

dave
Right now your command is re-encoding the original audio.  This creates a loss in quality because you are (most likely) going from a lossy format to another lossy format.  A better way to do this is to just copy the audio stream:
```
ffmpeg -i input.flv -acodec copy -vn output.flv
```

---

