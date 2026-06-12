---
title: "What's in your .emacs file?"
date: 2010-01-07
forum: The Cafe
---

### Post by Barriehie on 2010-01-07
Might find some cool stuff!

.emacs
```

(server-start)

(setq custom-file1 "~/emacs/barrie-start/.emacs-custom.el")
(load custom-file1)

```

.emacs-custom.el
```

;;
;; .emacs-custom.el
;;


;; Add to the load path
(add-to-list 'load-path (expand-file-name "~/emacs/barrie-start"))
(require 'multi-scratch)


;; Setup PHP mode
(setq auto-mode-alist
     (cons '("\\.php\\'" . php-mode) auto-mode-alist))


;; Force shell to ansi colors / clean shell displays!
(autoload 'ansi-color-for-comint-mode-on "ansi-color" nil t)
(add-hook 'shell-mode-hook 'ansi-color-for-comint-mode-on)


;; Alias' via environment vars.
(setenv "myfile" "~/emacs/barrie-start/.emacs-custom.el")
(setenv "baseinit" "~/.emacs")


;; Use a color theme
(require 'color-theme)
(color-theme-euphoria)
(setq color-theme-is-global t)


;; Load Path Additions
(normal-top-level-add-to-load-path
     '("~/emacs" "~/emacs/el"))


;; Setup TRAMP mode
(setq tramp-default-method "ssh")
(setq tramp-default-user "root")
(setq tramp-default-host "localhost")
(setq tramp-shell-prompt-pattern "^.*>$")
(setq tramp-chunksize 500)

(defun my-tramp-header-line-function ()
;;    (when (string-match "^/ssh.*$" default-directory)
    (when (string-match "^/ssh:root.localhost.*$" default-directory)
    (setq header-line-format
	  (format-mode-line ">>-----> THIS BUFFER IS VISITED WITH ROOT PRIVILEGES <-----<<"
			    'font-lock-warning-face)))
                            '(mode-line ((t (:background "Red")))))

(add-hook 'find-file-hooks 'my-tramp-header-line-function)
(add-hook 'dired-mode-hook 'my-tramp-header-line-function)

;; TRAMP beep when done downloading files
(defadvice tramp-handle-write-region
            (after tramp-write-beep-advice activate)
           " make tramp beep after writing a file."
           (interactive)
           (beep))
          (defadvice tramp-handle-do-copy-or-rename-file
            (after tramp-copy-beep-advice activate)
           " make tramp beep after copying a file."
           (interactive)
           (beep))
          (defadvice tramp-handle-insert-file-contents
            (after tramp-copy-beep-advice activate)
           " make tramp beep after copying a file."
           (interactive)
           (beep))

;; F5 Opens a new frame for SSH login.
;;(global-set-key [(f5)] (lambda() 
;;     (interactive)(find-file-other-frame "/ssh:root@localhost:")))


;; Set ALL files to UNIX line endings
(add-hook 'find-file-hook 'find-file-check-line-endings)
(defun dos-file-endings-p ()
  (string-match "dos" (symbol-name buffer-file-coding-system)))
(defun find-file-check-line-endings ()
  (when (dos-file-endings-p)
    (set-buffer-file-coding-system 'iso-latin-1-unix t)
    (set-buffer-modified-p nil)))


;; To use manually: M-x doc-mode
;; a mode designed for editing text file documents that contain a lot
;; of text to spell check, etc.
(defun doc-mode ()
  (interactive)
  (text-mode)       ;; use regular text mode
  (auto-fill-mode))  ;; wrap lines
  ;; (refill-mode)  ;; wrap lines (more aggressive)
  ;;(flyspell-mode))  ;; underline misspelled words
                    ;; run M-x flyspell-buffer for it to underline all
                    ;; words in the file instead of the words your
                    ;; cursor moves over.


;; Modeline settings
;; Show 24-hour time and date on status bar
(setq display-time-24hr-format t)
(setq display-time-day-and-date t)
(display-time)


;; Turn on garbage collection messaging
(setq garbage-collection-messages t)


;; Highlight the current line
(global-hl-line-mode 1)


;; Show line and column number
(line-number-mode 1)
(column-number-mode 1)


;; Typing "yes" or "no" takes too long---use "y" or "n"
(fset 'yes-or-no-p 'y-or-n-p)


;; Don't beep at me
(setq visible-bell t)


;; default coding
(prefer-coding-system 'utf-8)


;; Goto column function
(defun goto-column-number (number)
"Untabify, and go to a column number within the current line (1 is beginning
of the line)."
(interactive "nColumn number ( - 1 == C) ? ")
(beginning-of-line)
(untabify (point-min) (point-max))
(while (> number 1)
 (if (eolp)
     (insert ? )
   (forward-char))
 (setq number (1- number))))


;; column numbers
(setq column-number-mode t)


;; Resize window on load
(setq initial-frame-alist
      `((left . 0) (top . 0)
        (width . 110) (height . 44)))


;; for emacs to insert spaces instead of tab chars
(setq-default indent-tabs-mode nil);


;; Set the font
(set-default-font "-adobe-courier-bold-r-normal--14-100-100-100-m-90-iso8859-1")


;; Turn on the menu bar
(menu-bar-mode 1)


;; disable splash screen and startup message
(setq inhibit-startup-message t)


;;  Global font lock mode ON
(global-font-lock-mode t)


;; No zoning!!!
(zone-when-idle 0)


;; Make the cursor blink
(blink-cursor-mode 1)


;; Line numbering macro
(fset 'linenumbers
   (lambda (&optional arg) "Keyboard macro." (interactive "p") (kmacro-exec-ring-item (quote ([134217848 115 101 116 110 117 45 109 111 100 101 return] 0 "%d")) arg)))


;; Bind to key F2
(global-set-key [f2] 'linenumbers)


;; save the editor state
;;(desktop-save-mode 1)
(desktop-save-mode 0)


;; Make emacs use the clipboard
(setq x-select-enable-clipboard t)
(setq interprogram-paste-function 'x-cut-buffer-or-selection-value)


;; Use the Printing Package
(require 'printing)
(pr-update-menus)


;; set the PDF printer as default
;;(setq printer-name "PDF_file_generator")
;;(setq printer-name t)
(setq ps-printer-name "PDF_file_generator")
(setq ps-printer-name t)


(defun print-to-pdf ()
  (interactive)
  (ps-spool-buffer-with-faces)
  (switch-to-buffer "*PostScript*")
  (write-file "/tmp/tmp.ps")
  (kill-buffer "tmp.ps")
  (setq cmd (concat "ps2pdf14 /tmp/tmp.ps " (buffer-name) ".pdf"))
  (shell-command cmd)
  (shell-command "rm /tmp/tmp.ps")
  (message (concat "Saved to:  " (buffer-name) ".pdf"))
  )


;; Numbered Backups
(setq version-control t)
(setq backup-directory-alist '(("." . "/home/barrie/emacs/backups")))


(put 'upcase-region 'disabled nil)


;; Setup bookmarks file
(setq bookmark-default-file "~/.emacs.d/bookmarks" bookmark-save-flag 1)


(custom-set-variables
  ;; custom-set-variables was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(column-number-mode t)
 '(display-time-mode t)
 ;; '(fringe-mode 0 nil (fringe))
 '(fringe-mode 5 t (fringe))
 '(scroll-bar-mode (quote right))
 '(show-paren-mode t)
 '(size-indication-mode t)
 '(speedbar-frame-parameters (quote ((minibuffer) (width . 20) (border-width . 0) (menu-bar-lines . 0) (tool-bar-lines . 0) (unsplittable . t) (set-background-color "black"))))
 '(transient-mark-mode t))
(custom-set-faces
  ;; custom-set-faces was added by Custom.
  ;; If you edit it by hand, you could mess it up, so be careful.
  ;; Your init file should contain only one such instance.
  ;; If there is more than one, they won't work right.
 '(background "blue")
 '(font-lock-builtin-face ((((class color) (background dark)) (:foreground "Turquoise"))))
 '(font-lock-comment-face ((t (:foreground "MediumAquamarine"))))
 '(font-lock-constant-face ((((class color) (background dark)) (:bold t :foreground "DarkOrchid"))))
 '(font-lock-doc-string-face ((t (:foreground "green2"))))
 '(font-lock-function-name-face ((t (:foreground "SkyBlue"))))
 '(font-lock-keyword-face ((t (:bold t :foreground "CornflowerBlue"))))
 '(font-lock-preprocessor-face ((t (:italic nil :foreground "CornFlowerBlue"))))
 '(font-lock-reference-face ((t (:foreground "DodgerBlue"))))
 '(font-lock-string-face ((t (:foreground "LimeGreen"))))
 '(font-lock-type-face ((t (:foreground "#9290ff"))))
 '(font-lock-variable-name-face ((t (:foreground "PaleGreen"))))
 '(font-lock-warning-face ((((class color) (background dark)) (:foreground "yellow" :background "red"))))
 '(highlight ((t (:background "Blue"))))
 '(list-mode-item-selected ((t (:background "gold"))))
 '(makefile-space-face ((t (:background "wheat"))))
 '(mode-line ((t (:background "Navy"))))
 '(paren-match ((t (:background "darkseagreen4"))))
 '(region ((t (:background "DarkSlateBlue"))))
 '(show-paren-match ((t (:foreground "black" :background "wheat"))))
 '(show-paren-mismatch ((((class color)) (:foreground "white" :background "red"))))
 '(speedbar-button-face ((((class color) (background dark)) (:foreground "green4"))))
 '(speedbar-directory-face ((((class color) (background dark)) (:foreground "khaki"))))
 '(speedbar-file-face ((((class color) (background dark)) (:foreground "cyan"))))
 '(speedbar-tag-face ((((class color) (background dark)) (:foreground "Springgreen"))))
 '(vhdl-speedbar-architecture-selected-face ((((class color) (background dark)) (:underline t :foreground "Blue"))))
 '(vhdl-speedbar-entity-face ((((class color) (background dark)) (:foreground "darkGreen"))))
 '(vhdl-speedbar-entity-selected-face ((((class color) (background dark)) (:underline t :foreground "darkGreen"))))
 '(vhdl-speedbar-package-face ((((class color) (background dark)) (:foreground "black"))))
 '(vhdl-speedbar-package-selected-face ((((class color) (background dark)) (:underline t :foreground "black"))))
 '(widget-field ((((class grayscale color) (background light)) (:background "DarkBlue")))))

```

---

