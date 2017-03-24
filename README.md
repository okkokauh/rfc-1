[![Build Status](https://travis-ci.org/omahoito/rfc.svg?branch=master)](https://travis-ci.org/omahoito/rfc)



# rfc
Request for Comments and Change process for ODA Application Interfaces

We are conforming with a classic RFC process to continuously maintain a dialogue with stakeholders and the developer community. https://en.wikipedia.org/wiki/Request_for_Comments

Please see https://github.com/omahoito/rfc/projects/1 for the progress of requests.

Current schemas are in https://simplifier.net/FinnishPHR

## <a name="profiling_guide"></a>Profiling guidelines

* Profiles define the structures of the resources, data types, extensions and constraints used in ODA FHIR API. Profile implementers are expected to be familiar with the HL7 guidelines: http://hl7.org/fhir/2017Jan/profiling.html
* Profile names start with project identifier "ODA" and the profile name must contain the resource and the special domain of the particular resource (if any). For example a care plan for customer's self care is named as "ODA self-CarePlan profile". 
* Profiles must be in XML format and their filenames must contain the profile name, for example ODA-self-CarePlan.profile.xml
* Profile name should be in PascalCase, not camelCase, i.e. "ODA CarePlan" as well as filenames ie. ODA-CarePlan.profile.xml
* For each profile there must be also an example resource in JSON format. Example resource demonstrates how the data elements are used and its name must match to the profile name, for example: ODA-self-careplan.example.json.
* Profiles must be compatible with HL7 FHIR STU3 standard.
* A constraining profile can only allow what the base profile allows. Limitations are described more detailed in HL7 FHIR standard: http://hl7.org/fhir/2017Jan/profiling.html#5.1.0.7
* Each profile must contain both the snapshot and differential components. The snapshot component shows all resource elements in one description and the differential component describes the differencies compared to the base profile.
* Documenting the profile elements: Profile element definitions (http://hl7.org/fhir/2017Jan/elementdefinition.html) contain elements describing what the element is, why it exists and how it should or could be used. These include:
  * definition: A narrative text containing full formal definition of the element. This is required for all modified extensions or profile elements.
  * comments: Comments and other relevant information about the use of this element. This is optional.
  * requirements: Description why this element exists. This is optional.
  * example: Example value for the element. This is optional.
  * For example, the "category" element of the self-careplan profile could have following element definitions:
    * definition: "Identifies what kind of plan this is to support differentiation between multiple co-existing plans; e.g. "Self-care", "Diabetes" etc."
	* comments: "Only allowed value is 'Self-care'"
	* requirements: "This allows filtering different kinds of care-plans"
  


## Data model


Data models of the following profiles:

* ActivityDefinition
  * Profile documentation [STU3](http://hl7.org/fhir/2017Jan/activitydefinition.html)
  * Example resource as [json](https://github.com/omahoito/rfc/blob/master/ODA-activitydefinition.example.json)

* Appointment
  * Profile as [xml](https://github.com/omahoito/rfc/blob/master/ODA-appointment.profile.xml)
  * Example resource as [json](https://github.com/omahoito/rfc/blob/master/ODA-appointment.example.json)
  * Profile documentation ([STU2](https://www.hl7.org/fhir/appointment.html), [STU3](http://hl7.org/fhir/2017Jan/appointment.html))
  * Relevant STU2 -> STU3 changes: type renamed to appointmentType
  * [Discussion](https://github.com/omahoito/rfc/issues/3)

* CarePlan
  * Profile as [xml](https://github.com/omahoito/rfc/blob/master/ODA-careplan.profile.xml)
  * Example resource as [json](https://github.com/omahoito/rfc/blob/master/ODA-careplan.example.json)
  * Profile documentation ([STU2](https://www.hl7.org/fhir/careplan.html), [STU3](http://hl7.org/fhir/2017Jan/careplan.html))
  * Relevant STU2 -> STU3 changes: participant deleted in STU2, careteam added in STU3
  * [Discussion](https://github.com/omahoito/rfc/issues/10)

* CareTeam
  * Example resource as [json](https://github.com/omahoito/rfc/blob/master/CareTeam.json)
  * Profile documentation [STU3](http://hl7.org/fhir/2017Jan/careteam.html)
  * Introduced in STU3
  * [Discussion](https://github.com/omahoito/rfc/issues/11)

* Communication, used in communication between patient and practitioner
  * Profile as [xml](https://github.com/omahoito/rfc/blob/master/ODA-communication.profile.xml)
  * Example resource as [json](https://github.com/omahoito/rfc/blob/master/ODA-communication.example.json)
  * Profile documentation ([STU2](https://www.hl7.org/fhir/communication.html), [STU3](http://hl7.org/fhir/2017Jan/communication.html))
  * Relevant STU2 -> STU3 changes: topic added in STU3
  * [Discussion](https://github.com/omahoito/rfc/issues/7)

* Consent, information about the patient's policy choices
  * Example resource as [json](https://github.com/omahoito/rfc/blob/master/ODA-consent-example.json)
  * Profile documentation [STU3](http://hl7.org/fhir/2017Jan/consent.html)
  
* Device, used to fill in the symptome questionnaire
  * Profile as [xml](https://github.com/omahoito/rfc/blob/master/ODA-device.profile.xml)
  * Example resource as [json](https://github.com/omahoito/rfc/blob/master/ODA-device.example.json)
  * Profile documentation ([STU2](https://www.hl7.org/fhir/device.html), [STU3](http://hl7.org/fhir/2017Jan/device.html))
  * Relevant STU2 -> STU3 changes: device minimum cardinality changed from 1 to 0 in STU3
  * [Discussion](https://github.com/omahoito/rfc/issues/1)

* MedicationStatement, information about medication the patient is using
  * Example resource as [json](https://github.com/omahoito/rfc/blob/master/ODA-medicationstatement.example.json)
  * Documentation [STU3](http://hl7.org/fhir/2017Jan/medicationstatement.html)

* Observation about body temperature, contains patient's temperature measurements
  * Profile as [xml](https://github.com/omahoito/rfc/blob/master/ODA-temperature-observation.profile.xml)
  * Example resource as [json](https://github.com/omahoito/rfc/blob/master/ODA-temperature-observation.example.json)
  * Profile documentation ([STU3](http://hl7.org/fhir/2017Jan/observation.html))

* Person - FinnishPatient. Person and patient information. Person-profile is based on the FHIR-standard's STU3-version, FinnishPatient on Kela's profile
  * Person: http://hl7.org/fhir/2017Jan/person.html
  * Kela's FinnishPatient-profile: https://simplifier.net/FinnishPHR/FinnishPatient/
  * Resources as json:
    * [Person](https://github.com/omahoito/rfc/blob/master/ODA-person.example.json)
    * [Patient](https://github.com/omahoito/rfc/blob/master/ODA-finnishpatient-patient.example.json)
  * [Discussion](https://github.com/omahoito/rfc/issues/6)

* Practitioner, professional who takes care of patient
  * Example resource as [json](https://github.com/omahoito/rfc/blob/master/ODA-practitioner.example.json)
  * Documentation [STU3](http://hl7.org/fhir/2017Jan/practitioner.html)

* Questionnaire
  * Example resource as [json](https://github.com/omahoito/rfc/blob/master/ODA-questionnaire.example.json)
  * Documentation [STU3](http://hl7.org/fhir/2017Jan/questionnaire.html)

* QuestionnaireResponse
  * Example resource as [json](https://github.com/omahoito/rfc/blob/master/ODA-questionnaireresponse.example.json)
  * Documentation [STU3](http://hl7.org/fhir/2017Jan/questionnaireresponse.html)



## Data model visualised

![](http://www.plantuml.com/plantuml/proxy?src=https://raw.githubusercontent.com/omahoito/rfc/master/ODA-PHR-Datamodel.plantuml?6) 
<!--- This generates a picture based on Resource.pantuml. To change the counter in the url above, i.e. deployment.md?13 -> deployment.md?14 --->


## Contributing

If you are interested in contributing new profiles, please feel free to do so. The profiles have been made with [Forge](https://fhir.furore.com/forge/), and the same tool can be used for further development or modification of existing profiles or creation of new ones. Please see the [Profiling section](#profiling_guide) for further information.

Contributions are done through pull requests. Profile files are checked with [xmllint](http://xmlsoft.org/xmllint.html) and [Travis](https://travis-ci.org/). Please add a validation test for the profile to the [validation script] (https://github.com/omahoito/rfc/blob/master/rfctravisscript.sh) together with the schema file that the profile is based on. Passing the validation test is a precondition for new profiles to be accepted.

Schema validation files for DSTU2 profiles are located [here](https://github.com/omahoito/rfc/tree/master/xsd/STU2/fhir-all-xsd) and files for STU3 can be found [here](https://github.com/omahoito/rfc/tree/master/xsd/STU3/fhir-all-xsd). The schema files end with a xsd suffix.
