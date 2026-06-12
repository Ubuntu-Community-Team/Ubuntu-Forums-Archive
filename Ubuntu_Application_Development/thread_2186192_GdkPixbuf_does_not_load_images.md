---
title: "Gdk::Pixbuf does not load images"
date: 2013-11-06
forum: Ubuntu Application Development
---

### Post by MaxSchererMax on 2013-11-06
Hi,

I'm trying to load a *.jpg image into a Gdk:: Pixbuf, but it fails and keeps telling me: Error interpreting JPEG image file (Wrong JPEG library version: library is 62, caller expects 80)


```

try{
    Gdk::Pixbuf::create_from_file(".../Test.jpg");
}
    catch(const Glib::FileError& ex) {
    std::cerr << "FileError: " << ex.what() << std::endl;
}
    catch(const Gdk::PixbufError& ex) {
    std::cerr << "PixbufError: " << ex.what() << std::endl;
}

```

The only installed versions  are libjpeg8 and libjpeg8-dev

I have a similar problem loading *.png images: GdkPixbuf-WARNING **: Bug! gdk-pixbuf loader 'png' didn't set an error on failure.
PixbufError: Failed to load image '.../Test.png': reason not known, probably a corrupt image file

The libpng versions are 12-dev and 12-0

I'm using Gtkmm-2.4-dev

Any idea on how to fix this?

---

