---
layout: respec
title: Modeling Educational Verifiable Credentials
respec: >
  {
    "name": "vc-edu-modeling",
    "status": "CG-DRAFT",
    "latest": "https://w3c-ccg.github.io/educational_vcs/spec/latest",
    "repository": "https://github.com/w3c-ccg/educational_vcs",
    "issues": "https://github.com/w3c-ccg/educational_vcs/issues",
    "group": {
      "name": "Credentials Community Group",
      "url": "https://www.w3.org/community/credentials/",
      "list": "public-credentials",
      "patentUri": "https://www.w3.org/community/about/agreements/cla/"
    },
    "editors": [
      {
        "name": "Your Name",
        "url": "https://example.com",
        "company": "Your Company",
        "companyURL": "https://example.com"
      }
    ],
    "bibliography": {
      "RDF-DATASET-NORMALIZATION": {
        "title": "RDF Dataset Normalization 1.0",
        "href": "http://json-ld.github.io/normalization/spec/",
        "authors": ["David Longley", "Manu Sporny"],
        "status": "CGDRAFT",
        "publisher": "JSON-LD Community Group"
      }
    }
  }
---

<section id="abstract">
  <p>
    Your specification abstract goes here.
  </p>
</section>

<section id="sotd">
  <p>
    This is an experimental specification and is undergoing regular
    revisions. It is not fit for production deployment.
  </p>
</section>

<section id="terminology">
  <h2>Terminology</h2>
  <p>
    Your specification terminology goes here.
  </p>
</section>

<style>
.red43 {
  color: red;
}
</style>

<p class="red43">Custom CSS is Supported!</p>

## Markdown is Supported !

<p>
Example link to bibliography here... [[RDF-DATASET-NORMALIZATION]].
</p>

#### Example:

```json
{
  "id": "did:example:123#key-0",
  "controller": "did:example:123",
  "type": "JsonWebKey2020",
  "publicKeyJwk": {
    "crv": "secp256k1",
    "kty": "EC",
    "x": "dWCvM4fTdeM0KmloF57zxtBPXTOythHPMm1HCLrdd3A",
    "y": "36uMVGM7hnw-N6GnjFcihWE3SkrhMLzzLCdPMXPEXlA"
  }
}
```

<section data-dfn-for="Foo" data-link-for="Foo">
  <h2>Goals</h2>

<p>
- Issue a set of representative educational credentials as a Verifiable Credentials, in a forward-looking manner (details below)
- If possible, generalize guidance for a range of Verifiable Credential pilots in other sectors
</p>

<h2>Problem Statement</h2>
<p>
Many Verifiable Credentials pilots in the education space are having to invent their own schemas, despite the wealth of previous art in the educational data standards communities. That is for multiple reasons:
- The focus of the VC community has been very much on the “envelope” and not the contents
- Educational data standards are not easily approachable in a general way to outsiders: where does one start depending on use case? locale?
- Educational data standards have rich domain-specific vocabularies, taxonomies, and ontologies, but may have additional assumptions that data has been exchanged between trusted authorities (directly from issuer/clearing house to relying party), and therefore are not clearly adaptable to minimized/selective disclosure schemes.

The [LER wrapper](https://cdn.filestackcontent.com/preview/FeqEJI3S5KelmLv8XJss) effort has bootstrapped the alignment of existing educational data standards via the LER/VC wrapper. This enables technology providers to build interoperable tooling at the wrapper/envelope level, staying agnostic to the contents, while enabling discoverability of metadata. This effort attempts to extend upon those efforts, enabling interoperability/mapping at the content level via enriched linked data.

This effort attempts to bridge the VC ecosystem to the robust work already done in the educational data standards space, to enable reuse of the great work done by experts in the space. Our main goal is discoverability of educational data standards frameworks, and informing implementors of how to use these in VCs. 

Our work will help inform VC-EDU pilots, but will be forwarded as recommendations to relevant educational data standards bodies, representatives of which are active in this group. Educational data standards bodies rely on validation through real world use, which the umbrella of the W3C-CCG can provide.

Lastly, this will attempt to address design challenges related to standards relying on the XML serialization format, which is not currently a supported serialization format in the VC data model, but is still needed for legal compliance for example in eIDAS legal signatures.
</p>

<h2>Requirements & Scope</h2>


<h3>Requirements</h3>

* We are targeting the Verifiable Credential data model
* This assumes use of linked data (e.g. RDF/JSON-LD)
* Specifically, we assume critical data fields (e.g. see working example 1) must use structured, machine readable content, but additional presentations may be included (e.g. machine-readable plus PDF for human readable/backcompat)
* Support display integrity for scenarios where a human is in the loop performing additional verification. 
* International-aware: do not restrict to US edu data standards

### Out of Scope
- Deeper/structural changes such as degree audits, learning pathways, or actual standardization prior to implementation.
- VC-EDU can only release draft recommendations, but the standardization work needs to happen in the proper SDO; e.g. IEEE CM4LTS (for ILR recommendations), IMS Global (for Open Badges recommendations), etc. We will coordinate with the proper SDOs to do that work


## Possible approaches/inspiration

* Open Badge as VC. Example, updated from Nate and Kim’s RWOT6 paper: [https://github.com/w3c-ccg/vc-examples/issues/7#issue comment-602912697](https://github.com/w3c-ccg/vc-examples/issues/7#issuecomment-602912697)
* LER wrapper
  * [LER wallet spec](https://cdn.filestackcontent.com/preview/FeqEJI3S5KelmLv8XJss)
  *   Pilots/examples will evolve on T3 LER Hub - [http://lerhub.org](http://lerhub.org/)
  * Schema.org terms/types?
  * schema:Person is an obvious one for learner
  * ob:Profile is a generic profile class based on schema.org terms that can represent either learners or organizations.
    * [https://schema.org/EducationalOccupationalCredential](https://schema.org/EducationalOccupationalCredential)
* CEDS
* CTDL and Credential Engine **(note “credential” terminology issue**)
  * [https://credreg.net/](https://credreg.net/): RDF-based schema for describing credentials and skills 
    * Examples of open badge and CLR references to CTDL: [https://credreg.net/quickstart/ilwrguide](https://credreg.net/quickstart/ilwrguide).  
    * Credential Finder: [https://credentialfinder.org/](https://credentialfinder.org/)
* Controlled vocabularies used in Europe published as linked open data:
  * [https://op.europa.eu/en/web/eu-vocabularies/europasstables](https://op.europa.eu/en/web/eu-vocabularies/europasstables)
  * [https://op.europa.eu/en/web/eu-vocabularies/esco](https://op.europa.eu/en/web/eu-vocabularies/esco)
  *   Particularly useful is that ISCED-F (thematic areas of UNESCO's international classification of education):
  *   [https://op.europa.eu/web/eu-vocabularies/at-dataset/-/resource/dataset/international-education-classification](https://op.europa.eu/web/eu-vocabularies/at-dataset/-/resource/dataset/international-education-classification)

## Working Example 1: Course/Program Certificate
### Examples from the Wild


<table>
  <tr>
   <td>

<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image1.png" width="" alt="alt_text" title="image_tooltip">

   </td>
   <td>

<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


<img src="images/image2.png" width="" alt="alt_text" title="image_tooltip">

   </td>
  </tr>
</table>


### Extracted Fields

<table>
  <tr>
   <td><strong>Field</strong>
   </td>
   <td><strong>Ex 1 Values</strong>
   </td>
   <td><strong>Ex 2 Values</strong>
   </td>
  </tr>
  <tr>
   <td>Accomplishment Type
   </td>
   <td>MicroMasters Certificate
   </td>
   <td>Verified Certificate
   </td>
  </tr>
  <tr>
   <td>Learner Name
   </td>
   <td>Matthew Tracker
   </td>
   <td>Jane Learner
   </td>
  </tr>
  <tr>
   <td>Achievement
   </td>
   <td>Supply Chain Management
   </td>
   <td>My First Coursera Course
   </td>
  </tr>
  <tr>
   <td>Issued Date
   </td>
   <td>April 2016
   </td>
   <td>May 14, 2013
   </td>
  </tr>
  <tr>
   <td>Certificate ID
   </td>
   <td>230842h...0827
   </td>
   <td>&lt;verification link?>
   </td>
  </tr>
  <tr>
   <td>??? Issuer
   </td>
   <td>EdX
   </td>
   <td>Coursera
   </td>
  </tr>
  <tr>
   <td>Course Provider
   </td>
   <td>MITx
   </td>
   <td>U Penn
   </td>
  </tr>
  <tr>
   <td>Other
   </td>
   <td>&lt;signatories>???
   </td>
   <td>
   </td>
  </tr>
</table>

### Approaches


#### Approach 1: ILR/LER Wrapper with Open Badges JSON-LD serialization + PDF and linked competency definitions

EXAMPLE showing 1 record expressed in 2 different formats (JSON-LD and PDF) in the payload. Using the OpenBadges serialization for the JSON-LD and with links to a credential defined in credentialengineregistry.org and competencies from the casenetwork.imsglobal.org.

**In github**: [https://github.com/w3c-ccg/vc-ed/blob/gh-pages/samples/openBadgeAsLer.json](https://github.com/w3c-ccg/vc-ed/blob/gh-pages/samples/openBadgeAsLer.json)



### Approach 2: Open Badge as Verifiable Credentials

Notes:

*   The issuer asserts that a learner (identified with a DID) "holds" or "hasAchieved" a particular defined achievement (here, an Open Badges BadgeClass)
*   The defined achievement that is asserted is described inline, though most BadgeClasses are also available to be retrieved in their latest updated form at their identifying "id" IRI when that IRI uses the http/https scheme.

**In github**: [https://github.com/w3c-ccg/vc-ed/blob/gh-pages/samples/openBadgeAsVc.json](https://github.com/w3c-ccg/vc-ed/blob/gh-pages/samples/openBadgeAsVc.json)


A second expression of similar JSON that uses only existing credentials and openbadges contexts (Not a final approach)


## Working Example 2: Diploma

Comments/Questions: 

*   Diplomas may be expressed with the same approaches as shown in Working Example 1, because Open Badges is already used to issue diplomas.
*   Are there any other target formats we should include? E.g. via Europass efforts? 
*   Any additional alignment frameworks we should include?


## Working Example 3: Transcript


### Options

VCWhich standard would we like to start with?


<table>
  <tr>
   <td><strong>Standard</strong>
   </td>
   <td><strong>GEO</strong>
   </td>
  </tr>
  <tr>
   <td>PESC+XML High School
   </td>
   <td>Adoption in US/Canada; interest abroad
   </td>
  </tr>
  <tr>
   <td>PESC+XML College Transcript standard
   </td>
   <td>Adoption in US/Canada; interest abroad
   </td>
  </tr>
  <tr>
   <td>EDI based standard governed by ANSI in fairly wide use handled by a system called SPEEDE
   </td>
   <td>??
   </td>
  </tr>
  <tr>
   <td><a href="https://github.com/emrex-eu/elmo-schemas/releases">ELMO</a>
   </td>
   <td>Europe
   </td>
  </tr>
</table>



### Implementation Options



*   LER Wrapper is an option; note that it includes XML as a string: [https://docs.google.com/document/d/1gBKx47cgxsUnTMLxqg6Poswp4-led3x51unUY42fKUU/edit#heading=h.4rbynbs3ok62](https://docs.google.com/document/d/1gBKx47cgxsUnTMLxqg6Poswp4-led3x51unUY42fKUU/edit#heading=h.4rbynbs3ok62)
*   Improving on XML-as-string would be a bit of work. I see 2 paths:
    *   Push to support XML as VC format
        *   This would be helpful in the near-term, and would benefit other XML-based standards
    *   Map PESC to JSON-LD
        *   Work has started in a PESC JSON-LD Task Force: [https://www.pesc.org/json-ld-task-force.html](https://www.pesc.org/json-ld-task-force.html)
        *   The VC-EDU community can help push this forward

## Working Example 4: EDCI

Related links/examples:

*   XML example: [EDCI example](https://github.com/european-commission-europass/Europass-Learning-Model/blob/master/edci_credential.xml) in [Europass github](https://github.com/european-commission-europass/Europass-Learning-Model)
*   JSON/LD (LER) example: See example E6 EUROPASS in the [T3 LER Wrapper document](https://cdn.filestackcontent.com/preview/FeqEJI3S5KelmLv8XJss)
*   EBSI: [https://ec.europa.eu/cefdigital/wiki/display/CEFDIGITAL/EBSI](https://ec.europa.eu/cefdigital/wiki/display/CEFDIGITAL/EBSI)

Comments/Questions:

*   This will have the same problem as in Working Example 3: they are currently using XML (as required for legally binding signatures), but the VC data model only describes JSON/JSON-LD formats.
*   An [Europass EDCI in JSON-LD example](https://ec.europa.eu/cefdigital/wiki/pages/viewpage.action?pageId=262505555) (related to Level 6 EQF)

## Working Example 5: Open Skills Assertion of ceasn:Competency

In this example, an issuer who is not necessarily the same as the definer of the competency asserts achievement of a competency or learning goal directly. This could enable direct match-up against a requirement on a job profile or learning pathway. Self-assertion of competency is also supported. There is no "BadgeClass"/"DefinedAchievement" intermediary class that must be defined in order to set out a specific learning opportunity, criteria, or authorized assessing body in order to make this claim.

**Notes**:

*   The “ceasn:” prefix/namespace comes from here: [https://credreg.net/ctdlasn/terms](https://credreg.net/ctdlasn/terms)
*   ceasn:Competency is defined here: [https://credreg.net/ctdlasn/terms#Competency](https://credreg.net/ctdlasn/terms#Competency)

**In github**: [https://github.com/w3c-ccg/vc-ed/blob/gh-pages/samples/openSkillsAssertion.json](https://github.com/w3c-ccg/vc-ed/blob/gh-pages/samples/openSkillsAssertion.json)


## Working Example 6: EMREX

EMREX is a network for exchanging assessments/results of education at any level. 

The owner of the result (student or former student) gets access to trusted sources of these data (diploma registries, student information systems,...) and can share data with a third party. This third party could be an employer as part of a recruitment process, a university when applying for admission or others.

The technical set up of EMREX is described here:

[https://emrex.eu/wp-content/uploads/2020/01/Technical-Guide-to-EMREX.pdf](https://emrex.eu/wp-content/uploads/2020/01/Technical-Guide-to-EMREX.pdf)

EMREX is using a XML-format called ELMO, which is based on standard data models for Learning opportunities. The basis for the data exchange is structured data representing the results the result owner wants to share, but ELMO can also hold additional documents like a signed pdf of a Diploma.

Comments/Questions:



*   This will have the same problem as in Working Example 3 and 4: they are currently using XML (as required for legally binding signatures), but the VC data model only describes JSON/JSON-LD formats.


## Working Example 7: Using a credential definition that exists in Credential Engine

**In github**: [https://github.com/w3c-ccg/vc-ed/blob/gh-pages/samples/credentialEngine.json](https://github.com/w3c-ccg/vc-ed/blob/gh-pages/samples/credentialEngine.json)

## Working Example 8: Use of EducationalOccupationalCredential (schema.org)

About this example:

*   Uses [https://schema.org/EducationalOccupationalCredential](https://schema.org/EducationalOccupationalCredential)
*   Note that it’s using “hasAchieved” instead of “hasCredential”, the latter of which already exists in schema.org. We are considering adding “hasAchieved”, as described above
*   This takes advantage of other schema.org types, including mapping credentialSubject to Person

**In github**: [https://github.com/w3c-ccg/vc-ed/blob/gh-pages/samples/educationalOccupationalCredential.json](https://github.com/w3c-ccg/vc-ed/blob/gh-pages/samples/educationalOccupationalCredential.json)

  
  <pre class="idl">
  interface Foo {
    attribute Bar bar;
    undefined doTheFoo();
  };
  </pre>
  <section>
    <h2><dfn>bar</dfn> attribute</h2>
    <p>When getting, the <a>bar</a> attribute returns you a 🍹.</p>
  </section>
  <section>
    <h2><dfn>doTheFoo(DOMString thing)</dfn> method</h2>
    <p>When called, <code>doTheFoo(<var>thing</var>)</code> it MUST behave as follows:</p>
    <ol class="algorithm">
      <li>If <var>thing</var>....</li>
      <li>Let <var>someProp</var>... of the [[!DOM]] spec.</li>
    </ol>
  </section>
</section>

<section id='conformance'>
  <!-- This section is filled automatically by ReSpec. -->
</section>
