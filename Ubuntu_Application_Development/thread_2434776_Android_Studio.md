---
title: "Android Studio"
date: 2020-01-10
forum: Ubuntu Application Development
---

### Post by Ownager on 2020-01-10
You can move my thread to the right place if you think I did wrong. By the way, what's environment variables for Android Studio? I keep trying to get it work properly. It keeps saying NDK version is unknown.

I tried to put them into ./bashrc in ${HOME} and /root

Environment variables like this 

export ANDROID_HOME=${HOME}/Android/Sdk
export PATH="${ANDROID_HOME}/tools:${PATH}"
export PATH="${ANDROID_HOME}/emulator:${PATH}"
export PATH="${ANDROID_HOME}/platform-tools:${PATH}"
export path="/usr/bin"

Am I missing anything? 

Thank you for your help

---

