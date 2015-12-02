PEP: XXX
Title: Linked Metadata for Python Software Packages
Version: $Revision$
Last-Modified: $Date$
Author: Wes Turner <wes.turner@gmail.com>
BDFL-Delegate:
Discussions-To:
    GitHub: https://github.com/pypa/interoperability-peps/issues/31
    Distutils SIG <distutils-sig@python.org>
Keywords: PEP426JSONLD, RDF, RDFa, JSON-LD, JSONLD, LinkedData, Linked
Data
Status: Draft
Type: Standards Track (?)
Content-Type: text/x-rst
Requires: 440, 426 (?)
Created: 1 Dec 2015
Post-History: 
Replaces: 345 (?)


.. contents:: 

Abstract
========

This PEP describes a mechanism for publishing and exchanging metadata
related to Python distributions. It includes specifics of the field names,
and their semantics and usage.

* Version 1.0 is specified in PEP 241.
* Version 1.1 is specified in PEP 314.
* Version 1.2 is specified in PEP 345.
  PEP 345 is to be considered the current (2015) packaging
  metadata format.

* Version 2.0 (draft) is specified in PEP 426
  PEP426 would/will significantly modify the JSON metadata
  format; adding additional fields for e.g. source code metadata
  and semantic dependencies.

* Version 3.0 (1.2 + [2.0] + Linked Data) (draft)
  is specified in this document.

  For purposes of practicality, because PEP 426 is still draft,
  this PEP will strive to convert first Version 1.2 PEP 345 metadata
  and then Version 2.0 (draft) PEP 426 metadata.
 
Version 3.0 Would Require

* metadata.json (Version 1.2 (345), Version 2.0 (426))
* metadata.jsonld (in addition to the existing metadata.json)

  * [ ] lookup-optimized JSON metadata keys -> JSON-LD ``@context``

* schema.pypa.io JSONLD ``@context``

  * 


Definitions
==============

Linked Data
    Linked Data is data linked with URIs; preferably in a format
    that is convertible to or already RDF (such as RDFa, JSON-LD,
    Turtle/Trig)

    TODO: ld-glossary

URI
    A URI (*Uniform Resource Indicator*) is a namespaced
    string with structured parts and delimiters
    for naming or identifying a resource.

    TODO: example

URN
    TODO: example

URL
    A URL (*Uniform Resource Locator*) is a **URI**
    identifying a retrievable resource.
   

RDF
    RDF (*Resource Description Framework*)

RDFa
    RDFa (*RDF-in-attributes*) is an open W3C format for including
    structured data inline with (presentational) HTML pages.

    * Search engines can and do parse RDFa (particularly with schema.org
      types and property/attribute/column URIs)

JSON-LD / #JSONLD
    JSON-LD (*JSON Linked Data*) is a format

Schema.org
    `<schema.org>`__ is a standard RDFS vocabulary of classes and
    properties for many different domains.

    * schema.org is maintained as RDFa; other formats are generated from
      the source RDFa representation.

      TODO: link

    * schema.org supports an extension vocabulary model; suggesting
      ``schema.[domain.tld]`` for URI namespaces and ``schema<...>:``
      for URI QNames (and URI CURIES).

      TODO: link


schema.org/SoftwareApplication
    + http://schema.org/SoftwareApplication

schema.org/Code
    + http://schema.org/Code



Features / Use Cases / TODO
=============================

Version 3.0 Would Enable

* Python Packaging RDF
  
  * | xmlns: https://schema.pypa.io
  * | xmlns: ``schemapy:``
 
  * @type: SoftwarePackage

    * @type: PythonPackage

  * @type: PythonPackageRelease

    * @type: Sdist
    * @type: Bdist
    * @type: Egg
    * @type: Wheel
    * @type: [Conda]

  * @type: Requirement

    * @type: PythonPackageRequirement
  
  * @type: Constraint

  * @type: PackageRepo

    * @type: PythonPackageRepo

      * @type: HostedPythonPackageRepo

        * eg: :ref:`PyPI`
        * eg: :ref:`Warehouse`
        * eg: [:ref:`DevPi`]

* [ ] schema.pypa.io (a ``gh-pages`` branch. sphinx?)

* [ ] Warehouse: metadata.jsonld extraction & indexing
* [ ] Warehouse: JSONLD HTTP GET views:
  https://warehouse.python.org/project/pip/jsonld

* [ ] Warehouse: JSONLD in the package [release] template:
  https://warehouse.python.org/project/pip

  .. code:: html
  
      <script type="application/ld+json">
      {"@context": {...},
       "@graph": {
      }}
      </script>

* [ ] Warehouse: RDFa in the package [release] template:
  https://warehouse.python.org/project/pip


.. [1] reStructuredText markup:
   http://docutils.sourceforge.net/

.. _PyPI: http://pypi.python.org/pypi/

.. _Warehouse: https://warehouse.python.org/


Copyright
=========

This document has been placed in the public domain.


..
   Local Variables:
   mode: indented-text
   indent-tabs-mode: nil
   sentence-end-double-space: t
   fill-column: 70
   End:
