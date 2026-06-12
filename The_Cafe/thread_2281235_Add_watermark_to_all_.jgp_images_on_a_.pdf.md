---
title: "Add watermark to all .jgp images on a .pdf"
date: 2015-06-05
forum: The Cafe
---

### Post by john409 on 2015-06-05
I am looking for a quickish way to add a watermark to all the images in a  pdf. I have a catalog that has about 30 images per page and is about 200  pages long, and I want to display it online, but want to protect the  images. I have found scripts for stripping all the images, and I have  found ways to apply watermarks to all of the images in a folder, but I  cannot find a way to watermark all of the images on a page.

Any suggestions?

---

### Post by HermanAB on 2015-06-05
The only program I know that can add watermarks to images is the imagemagic program 'convert'.

---

### Post by john409 on 2015-06-05
It looks like 'convert' won't do quite what I need. I already found a way to remove the .jpg images from the entire .pdf, what I am looking for is a way to leave the .jpg images in their position on the .pdf page but with a .png watermark overlaying each image.

Surely someone has figured out a way to do this! ? ... please?

---

### Post by SeijiSensei on 2015-06-06
I think this problem is harder than you realize.  Other than disassembling the PDF into its components, watermarking the images, and reassembling the PDF, I can't think of a way to do what you want.

Now if the images were nicely arranged so that they always appear in the same places on each page, then you might be able to create a single watermark layer that you could superimpose on each page.  That's just a guess, though.  

A more tedious method would be to use GIMP which can read PDF files.  Once the file is imported, you could add the watermark layers manually.

Do you have the original file that was used to create the PDF?  If so, then you could replace the images in that with the watermarked versions and export the file to a new PDF.  If this was done in a professional publishing application like Pagemaker, you probably will need to use Windows.

---

### Post by john409 on 2015-06-07
Thank you for the responses.

I was afraid it might not be simple.

&#55357;&#56847;

---

### Post by dragonfly41 on 2015-06-09
Here is one approach which works on the disassembled PDF (text + images).  
The watermark text style is not able to be customised but it works
by adding a watermark to each page in the document containing the imported images..

(1) Open a new document in LibreOffice Writer.

(2) Import your source *.jpeg images into the document.

(3) Export document as PDF but optionally in Export options

     set watermark text
     set password for opening the PDF file
     and see other options such as blocking printing
     
You could also try Scribus (in Ubuntu Software Centre) for adding watermarks to your catalogue.

---

