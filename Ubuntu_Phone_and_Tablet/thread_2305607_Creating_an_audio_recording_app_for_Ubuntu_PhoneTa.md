---
title: "Creating an audio recording app for Ubuntu Phone/Tablet"
date: 2015-12-07
forum: Ubuntu Phone and Tablet
---

### Post by moma on 2015-12-07
Hello,
I have just started to work with the Ubuntu SDK and would like to code a small audio-recorder for my Ubuntu Phone.

Question:
Should I use the Gstreamer library or QT`s Multimedia and QAudioRecorder classes?

Gstreamer in QT:
[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/qt-gstreamer/html/index.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/qt-gstreamer/html/index.html)

QT Multimedia and QAudioRecorder:
[http://doc.qt.io/qt-5/multimedia-examples.html](http://doc.qt.io/qt-5/multimedia-examples.html)

I do not know what backend (phonon, gstreamer, ?) the QT Multimedia uses.

Obrigado pela sua resposta.
 Moma, Portugal

---

### Post by jtappin on 2015-12-08
Unless you want to do it to learn about app development, there is already such an app: just called "recorder" in the Ubuntu app store.

---

### Post by moma on 2015-12-08
Yep, I want to learn.
I want to create my own.

Ok, I made a first test with QAudioRecorder.
But it only provides "audio/pcm" format.

In the following code, the codecList contains only "audio/pcm".
The code does record well, but the output is "test3.mp3.wav" file .  I was expecting MP3 format, not WAV.

```
MainWindow::MainWindow(QWidget *parent) : QMainWindow(parent),  ui(new Ui::MainWindow)
{
    ui->setupUi(this);

    recorder = new QAudioRecorder(this);

    // Check codecs
    QStringList codecList = this->recorder->supportedAudioCodecs();

    foreach (const QString &str, codecList) {
        qDebug() << str;
    }
    // This lists only "audio/pcm"

    // List available audio input devices
    QString defInput = recorder->defaultAudioInput();
    qDebug() << "Default input devices:" << defInput << endl;

    QStringList inputs = recorder->audioInputs();
    foreach (QString input, inputs) {
        QString desc= recorder->audioInputDescription(input);
        qDebug() << input << " / " << desc;
    }

    // Settings.

    // Set input (audio) device to record from
    recorder->setAudioInput(recorder->defaultAudioInput());
    // You can take a list of all pulseaudio-devices with: 
    // $ pactl list | grep -A3 'Source #'
    // $ pactl list short sources | cut -f2
    // 
    // And a list of Alsa-device names with:
    // $ aplay -L 

    this->audioSettings.setCodec("audio/mpeg");
    this->audioSettings.setQuality(QMultimedia::HighQuality);
    this->recorder->setEncodingSettings(this->audioSettings);
    this->recorder->setContainerFormat("mp3");

    this->recorder->setOutputLocation(QUrl::fromLocalFile("test.mp3"));

    recorder->record();
    //recorder->pause();
    //recorder->stop();

   // This produces "test3.mp3.wav" file.

}
```

---

### Post by moma on 2015-12-09
EDIT:

I installed some additional QT packages and updates. Now the recorder has these codecs.
"audio/mpeg"
"audio/vorbis"
"audio/GSM"
"audio/PCM"
"audio/AMR"

Looks promising.

However, the audiodevices-example sees only "audio/pcm". 
[http://doc.qt.io/qt-5/qtmultimedia-audiodevices-example.html](http://doc.qt.io/qt-5/qtmultimedia-audiodevices-example.html)

---

