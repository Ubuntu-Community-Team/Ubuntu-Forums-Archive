---
title: "Aliases Problem"
date: 2012-01-06
forum: Server Platforms
---

### Post by memaster3 on 2012-01-06
My aliases file is giving an error when I log in. Here's the exact text of the error.

```
-bash: /home/jon/.bashrc: line 13: unexpected EOF while looking for matching `''
-bash: /home/jon/.bashrc: line 14: syntax error: unexpected end of file
```

and here's what's in the aliases file.

```
# Server Aliases File

# Edit the bashrc alias file
alias aliases='pico .bashrc'

# Go up a level
alias ..='cd ..'

# Print "Execution Sucessful!" to the terminal
alias sucessful='echo Execution Sucessful!

# Speedtest a download
alias speedtest='curl -o /dev/null http://speedtest.wdc01.softlayer.com/downloads/test100.zip'
```

I've tried everything, short of deleting it and starting over, and would like some help to figure out what's causing this.

Thanks for the help!

---

### Post by m_duck on 2012-01-06
You just seem to be missing the closing single quote on the end of the 'alias successful...' line (line 10). The error is shown at a later line, because bash reads the first quote on line 13 as the closing quote to the previous alias, ergo the last alias line is read as nonsense.

HTH

---

