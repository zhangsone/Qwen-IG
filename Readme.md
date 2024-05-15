<!--
 * @Author: sone 1607382074@qq.com
 * @Date: 2024-03-23 21:41:50
 * @LastEditors: sone 1607382074@qq.com
 * @LastEditTime: 2024-03-25 21:31:14
 * @FilePath: \undefinede:\五科\论文相关\datasets\Readme.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
# Qwen-QA: A Qwen-based Question Answering Generation Model for Instruction Tuning

All data sets will be open sourced after the paper is accepted.

The following is an introduction to the data set.

## 01 train

### Dataset summary
This folder contains bilingual training sets in English and Chinese, and the two training sets are randomly mixed during formal training. en_train contains 8289 pieces of data and ch_train contains 6498 pieces of data.

### language
Chinese(ch),English(en)

### Dataset Structure
An example of 'train' looks as follows.
```
{
    "instruction":"Please use the input text below to generate a question and answer pair. Output format requirements \n Question: {}, Answer: {}",
    "input":"In order to reduce online security threats, we can take a variety of measures. First, implementing a strong password strategy is key. Make sure users use complex and unique passwords and change them regularly. Second, limiting access to critical systems is also very important. Only authorized personnel can access sensitive information and systems. In addition, the use of two-factor authentication can provide an additional level of security. In addition, regular security audits and scans can help uncover potential vulnerabilities and threats. Encrypting confidential data prevents unauthorized access. Disabling unnecessary services can reduce the attack surface. Finally, regular patching of software and systems is also necessary to fix known security vulnerabilities. In addition to these technical measures, it is also very important to educate users about net-work security and phishing strategies. By improving the user's security awareness and knowledge level, it can effectively reduce the occurrence of online security threats",
    "output":"Question：What can be done to reduce online security threats?，Answer：1. Implement a strong password strategy. \n2. Limit access to critical systems. \n3. Use two-factor authentication. \n4. Conduct regular security audits and scans. \n5. Encrypt confidential data. \n6. Disable unnecessary services. \n7. Regular patching of software and systems. \n8. Improve user network security awareness and phishing strategies. "
}
{
    "instruction":"Please use the input text below to generate a question and answer pair. Output format requirements \n Question: {}, Answer: {}",
    "input":"In machine learning, the purpose of clustering is mainly to divide large data sets into smaller subsets, each of which contains similar data points.  This partitioning is achieved by clustering algorithms that use statistical methods to group data points based on similarity such as distance.  In this way, we can better understand and analyze the data, as some data points may not be obvious and only found by clustering.  Moreover, clustering can be used for classification and prediction tasks, thus improving the efficiency and accuracy of machine learning.",
    "output":"Question： What is the purpose of clustering in machine learning? ，Answer： The purpose of clustering in machine learning is to divide large data sets into smaller subsets, each of which contains similar data points.  The clustering algorithm uses statistical methods to group data points based on similarity such as distance.  By grouping data points, clustering can be used to classify, predict, and find relationships between data points, which may not be apparent by looking at the data alone."
}
{
    "instruction":"Please use the input text below to generate a question and answer pair. Output format requirements \n Question: {}, Answer: {}",
    "input":"Entropy is a very important concept in thermodynamics. It is used to measure the randomness of a system and its ability to produce useful work. This concept is closely related to the second law of thermodynamics. According to this law, the entropy of a system does not decrease over time unless we add energy to it. Entropy is therefore crucial to understanding how heat transfer and chemical processes occur in nature.",
    "output":"Question: What is the concept of entropy in thermodynamics?， Answer: In thermodynamics, entropy is a measure of the randomness of a system and its ability to produce useful work. It is closely related to the second law of thermodynamics, which states that the entropy of a system never decreases with time unless energy is added to the system. Entropy is essential for understanding how heat transfer and chemical processes occur in nature."
}
```
The data fields are the same among all splits.
* instruction:This field is used to describe the task type and instructions
* input:Input text knowledge
* output:The result of the model response according to the requirements of the instruction

## 02 test

Because different test sets compare different models, we divided en_test and ch_test in the test phase.
To ensure consistency, we take the same instructions during the testing phase as we did during the training phase.

## 03 perdict_result

This folder contains prediction files for all models

### Field structures for different models

#### baichuan2、LLaMA2、Qwen-QA
* id:Test set id
* input:Input text knowledge
* label:Test set answer
* predict:The response generated by the model

#### t5、mt5-base、mt5-small
* idx:Test set id
* input:Input text knowledge
* reference:Test set answer
* question:The question generated by the model response
* answer:The answer generated by the model response

#### PAQ
* question:The question generated by the model response
* answer:The answer generated by the model response


## 04 Examples of different model generation instruction sets
```
context:"In the computer field, the processor is one of its core components. For many users, understanding and differentiating between different types of processors is an important skill. When we talk about the two types of computer processors, we first need to understand their basic characteristics. These features include, but are not limited to, clock speed, number of cores, performance, and power consumption. The clock speed refers to the number of instructions the processor can execute per second, while the number of cores indicates the number of tasks the processor can handle simultaneously. Performance and power consumption are important indicators to measure processor efficiency and power consumption. In addition, to gain a deeper understanding of the differences between the two processors, we can also compare them to other processors of the same type. In this way, we can more accurately determine the differences between them."

T5:
{
    question:"How do you distinguish between two types of computer processors?"
    answer:"The differences between the two types of computer processors can be determined by analyzing different characteristics such as clock speed, number of cores, performance, power consumption, and so on. In addition, you can compare the processor to other processors of the same type to determine the differences between them."
}

PAQ:
{
    question:"What do we need to know when we talk about two types of computer processors?"
    answer:"Complex understanding of their basic properties"
}

ChatGLM3:
{
    question:"What are the basic characteristics of a computer processor?"
    answer:"Including but not limited to clock speed, number of cores, performance, and power consumption."
}

Baichuan2:
{
    question:"Please briefly describe the basic characteristics of the two computer processors."
    answer:"The basic characteristics of a processor include clock speed, number of cores, performance and power consumption."
}

Qwen-QA:
{
    question:"How do you distinguish between the two types of computer processors?"
    answer:"The difference between the two types of computer processors can be determined by analyzing different characteristics such as clock speed, number of cores, performance, power consumption, and so on. In addition, you can compare the processor to other processors of the same type to determine the differences between them."
}
```
