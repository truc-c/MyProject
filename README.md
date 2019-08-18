# Silence .eaf Audio Segments

**University of California, Los Angeles**\
Communications Department\
Lab of Professor Anne Warlaumont

**Mentors:**\
Anne Warlaumont\
UCLA Professor\
https://www.annewarlaumont.org

Kyle MacDonald\
UCLA Postdoc Researcher\
https://kemacdonald.com

**Contributors:**\
Anne Warlaumont

Kyle MacDonald

Vicky Chen\
Double Major: Business Economics and Communication\
UCLA Anderson School of Management: Masters of Science in Business Analytics

Curt Chang\
Major: Commuications w/ Computing Specialization


Greetings,

Thank you for taking the time to take a look at our project!

Our most important task as Research Assistants is to ensure the privacy of particpants as we vet audio recordings.  ELAN is
a software tool that we utilize to annotate time selections of the sensitive information during the vetting process.  ELAN
creates a A file extension of type (.eaf) that containing annotations and their associated time segments.  

Opening the file (.eaf) with a text editor displays the ELAN information (annotation and time selections) in XML format.  We
utilize Python and the module [xmltodict](https://pypi.org/project/xmltodict/) to extract this information, such as annotated text, selected tiers, time slots, etc.  

After we have extracted the time segments (from the .eaf file) that contain the sensitive information of the
participants, we use the module [pydub](https://pypi.org/project/pydub/) to silence out those time segments.

P.S.

Special thank you to James Robert (http://jiaaro.com) for his guidance on using the pydub module.


## Modules used:
- [xmltodict](https://pypi.org/project/xmltodict/)
- [pydub](https://pypi.org/project/pydub/)
- os
- sys
- platform
- pprint

## Sample audio, Sample .eaf file, and Sample code:
- [sample audio](https://github.com/truc-c/Comm-Lab-Project/blob/master/sample_audio.wav)
- [sample .eaf](https://github.com/truc-c/Comm-Lab-Project/blob/master/ELAN_sample.eaf)
- [sample code](https://github.com/truc-c/Comm-Lab-Project/blob/master/sample_code.py)

The sample_audio.wav is a 30 second audio of Curt Chang counting from 1 to 30.\
The ELAN_sample.eaf are annotations that Curt Chang has made using ELAN.\
The software is available for download here: [ELAN](https://tla.mpi.nl/tools/tla-tools/elan/)\
The sample coded provided is ran in MacOS terminal along with .eaf file name.
- for example: python sample_code.py /path/to/file/name/sample.eaf

## Documentation:
Here are some examples of how to use the functions and their output.

### imports:
```python
from myproject import parsing_functions as pf
import xmltodict
import pprint
import sys
import platform
```

- myproject is a folder where we stored our parsing_functions.py
- `xmltodict` module is used to create a xml object from our .eaf file
- `pprint` module helps with the format of the output
- `sys` module is used to provide an additional argument (path to eaf file) when running our python code in terminal
- `platform` is used to check our python version

### code example of functions and their output:
get_tier_names(eaf_obj) returns a list of all the TIER_ID's in the .eaf file\
(e.g.,[ELAN_sample.eaf](https://github.com/truc-c/Comm-Lab-Project/blob/master/ELAN_sample.eaf) contains 2 TIER_ID's, cut and bookmark)
```python
tier_name_list = pf.get_tier_names(eaf_obj)

print(tier_name_list)             # output: [cut,bookmark]
```

py_version_input(python_version,tier_name_prompt) selects the input format depending on the python version and returns a string
```python
python_version = int(platform.python_version()[0])
tier_name_prompt = 'Enter tier name: '
user_input = pf.py_version_input(python_version,tier_name_prompt)
```
