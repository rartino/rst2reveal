#######################
rst2reveal rartino fork
#######################

ReST to Reveal.js translator
----------------------------

This is a fork of **rst2reveal** from https://github.com/vitay/rst2reveal

**rst2reveal** is intended to transform regular reStructuredText (ReST) text files to HTML5 slides using the `Reveal.js <https://github.com/hakimel/reveal.js>`_ Javascript library developped by `Hakim El Hattab <http://hakim.se>`_. 

The intent of this forked version is to introduce changes that makes it easier to work with the latest version of reveal.js, and to provide access to all its features via the ReST file. Primary changes:

* Some extra directives in the .conf file to allow
    
  - Specifying paths to reveal.js, etc.
  - Completely configure the initialization step of reveal.js, allow loading plugins, etc.
  - Allow configuration of attibutes for the <slide> tag for the title slide

* Edits to the parser to make it work fully with utf-8 

* Extensions to the ..class directive makes it possible to set html attributes, and for titles that generate slides (i.e., sections) separate attributes can be set on each.
  The changes to class makes its one argument optional, and adds to options: attributes and slide-attributes. Here things like data-background can be set. The syntax is
  a python dictionary. Use, e.g., {'data-background-video':None} to set a boolean attribute.

* Two more column types are added: 'main' and 'side' that provide a golden ratio division between a broader column and a side column.

* Third level slide headlines are not shown in the actual presentation, but are meant to just be used as short 'category' names in which slides are grouped.
  This works very well with plugins that let you navigate over categories.
  Headlines to be shown on the actual slides needs to be fourth level. So if you want the same title, just repeat it on the fourth level.
  
Other reveal.js features should be accessible via raw::html directives.
	
Unlike the original **rst2reveal**, this fork does not include Reveal.js.

Dependencies
------------

In addition to Python 2.6 or 2.7 (not 3.x yet), **rst2reveal** requires the following packages:

* `docutils <http://docutils.sourceforge.net/>`_

* `setuptools <http://pypi.python.org/pypi/setuptools>`_

* `Reveal.js<https://github.com/hakimel/reveal.js>`_
  
If you want to display code in your slides, it is strongly advised to have `pygments <http://www.pygments.org>`_ installed for syntaxic color highlighting in many languages.

To directly generate plots within the ReST script, you will need `Matplotlib <http://matplotlib.org/>`_ (version >= 1.1) installed.

Installation
------------

Simply clone the git repository and install it using setuptools::

    $ git clone https://github.com/rartino/rst2reveal.git
    $ cd rst2reveal
    $ sudo python setup.py install
    
**rst2reveal** has been tested only on GNU/Linux systems, but perhaps it works on other platforms.

Usage
-----

You can go in the ``docs/`` subfolder and compile the presentation::
    
    cd docs/
    (update presentation.conf to setup paths to your reveal.js)
    rst2reveal presentation.conf

Command-line options
--------------------
    
You can get a summary of command-line options by typing::

    rst2reveal --help
