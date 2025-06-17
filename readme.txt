This package contains an emacs major mode for editing SGML and XML
DTDs.  The current revision is 0.8 beta 1, dated 1st September, 2001.

The tdtd home page is http://www.menteith.com/tdtd/


* MANIFEST

File                            Contents

readme.txt                      The file you are reading
dot_emacs                       Some things for your .emacs file
tdtd.el                         A collection of DTD-related procedures
tdtd-font.el                    Font lock keywords for DTDs
tdtd-font-maker.el              Data and procedure to create tdtd-font.el
tdtd-make-regexp.el             Used by tdtd-font-maker.el
changelog.txt                   List of changes
tutorial.txt                    A tutorial on using dtd-mode


* FEATURES

 - Standalone mode for editing DTDs;

 - "TAGS" menu for locating declarations within the current buffer;

 - `dtd-etags' function for creating Emacs TAGS files for easy lookup
   across multiple files of any element, parameter entity, or
   notation's definition using Emacs's built-in tag-lookup functions;

 - `dtd-grep' function for searching files that shares a file history
   with `dtd-etags' for easy searching of the same files with both
   functions;

 - Specific font lock highlighting of declarations in XML DTDs, SGML
   DTDs, SGML Declarations, and System Declarations so that the
   important information stands out;

 - XML-specific behaviour that, at user option, is triggered by
   automatic detection of the XML Declaration; 

 - Functions for writing and editing element, attribute, internal
   parameter entity and external parameter entity declarations and
   comments to ease creating and keeping a consistent style; and

 - Elements and parameter entity names referenced in declarations are
   stored in minibuffer history to minimise retyping in new
   declarations.

dtd-mode references `sgml-validate' for its validation function.  Use
with Lennart Staflin's psgml package is recommended.

Use with resize-minibuffer-mode is also recommended.

The "TAGS" menu is only available if you have imenu.el.

dtd-mode was tested using NTEmacs 20.7.1.

* FORMATTING VARIABLES

dtd-mode uses many user-definable variables to control the formatting
of declarations, some of which are shown in the following examples:

                        dtd-comment-start-column    dtd-dtd-max-column
                        |                    dtd-comment-max-column  |
                        |                                         |  |
<!--                    This is a comment                          -->

           dtd-element-name-column
           |            dtd-element-tag-ommission-column
           |            |   dtd-element-content-spec-start-column
           |            |   |dtd-element-content-spec-continuation-column
           |            |   ||                      dtd-dtd-max-column
           |            |   ||                                       |
<!ELEMENT  element-tag  - - (insert, your, content, specification,
                             here)                                   >

* BUG REPORTS/ENCHANCEMENTS

I would be glad to accept bug reports and/or enhancements.  Use
`dtd-submit-bug-report'.

* INSTALLATION

1. Unzip the distribution.

   This should extract the files listed in the manifest above.

   The files have DOS-style line breaks.  You may need to use "unzip
   -a" or "gunzip -a" to convert the line ends in the files to your
   local convention.

2. Copy the tdtd.el and tdtd-font.el files to somewhere on your emacs
   `load-path'; for example, your emacs site-lisp directory (e.g.,
   /usr/local/lib/emacs/site-lisp).

   XEmacs users also need to make sure that they have imenu.el
   installed before they can use the "Goto" menu.

3. Byte compile tdtd.el and tdtd-font.el using M-x byte-compile-file
   and supplying the path name of each file.

   The provided makefile also has rules for byte-compiling the files.

   If you byte-compiled a previous version of tdtd.el and
   tdtd-font.el, then you must byte-compile the new files (or remove
   the old .elc files) so that autoload loads the correct versions.

   If you do not have imenu.el, you may receive a "assignment to free
   variable imenu-create-index-function" warning when you byte compile
   tdtd.el.  You will, however, be able to use the compiled tdtd.elc
   without error (and without the "Goto" menu).

   You do not need tdtd-font-maker.el or make-regexp.el in order to
   use tdtd.  They are provided in case you want to modify the
   font-lock regular expressions and remake tdtd-font.el.

4. Add the elisp code in dot_emacs to your .emacs file.

   Windows users that are not using a Unix-like shell (e.g. bash)
   should uncomment and use the definition of dtd-etags-regex-option
   in dot_emacs.

5. When you visit a file with an extension of .dtd, etc., dtd-mode
   will automatically be loaded.


* MAKING tdtd-font.el

tdtd-font.el is created by tdtd-font-maker.el.  You should not need to
remake tdtd-font.el unless you have tinkered with the regular
expressions in tdtd-font-maker.el.

1. Load file `tdtd-font-maker.el'.

2. Execute `dtd-make-tdtd-font'.

   tdtd-font.el is created in the current directory.

-----
Tony Graham
17 August 2007

