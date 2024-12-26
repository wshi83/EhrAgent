<div align="center">
<h1> ⚕️EHRAgent🤖 </h1>
</div>

The official repository for the code of the paper ["EHRAgent: Code Empowers Large Language Models for Complex Tabular Reasoning on Electronic Health Records"](https://arxiv.org/abs/2401.07128). EHRAgent is an LLM agent empowered with a code interface, to autonomously generate and execute code for complex clinical tasks within electronic health records (EHRs). The project page is available at [this link](https://wshi83.github.io/EHR-Agent-page/).

### Features

- EHRAgent is an LLM agent augmented with tools and medical knowledge, to solve complex tabular reasoning derived from EHRs;
- Planning with a code interface, EHRAgent enables the LLM agent to formulate a clinical problem-solving process as an executable code plan of action sequences, along with a code executor;
- We introduce interactive coding between the LLM agent and code executor, iteratively refining plan generation and optimizing code execution by examining environment feedback in depth.

### Data Preparation

We use the [EHRSQL](https://github.com/glee4810/EHRSQL) benchmark for evaluation. The original dataset is for text-to-SQL tasks, and we have made adaptations to our evaluation. We release our clean and pre-processed version of [EHRSQL-EHRAgent](https://drive.google.com/file/d/1EE_g3kroKJW_2Op6T2PiZbDSrIQRMtps/view?usp=sharing) data. Please download the data and record the path of the data.

### Credentials Preparation
Our experiments are based on OpenAI API services. Please record your API keys and other credentials in the ``./ehragent/config.py``. 

### Setup

See ``requirements.txt``. Packages with versions specified in ``requirements.txt`` are used to test the code. Other versions that are not fully tested may also work. We also kindly suggest the users to run this code with Python version: ``python>=3.9``. Install required libraries with the following command:

```bash
pip3 install -r requirements.txt
```

### Instructions

The outputting results will be saved under the directory ``./logs/``. Use the following command to run our code:
```bash
python main.py --llm YOUR_LLM_NAME --dataset mimic_iii --data_path YOUR_DATA_PATH --logs_path YOUR_LOGS_PATH --num_questions -1 --seed 0
```

We also support debugging mode to focus on a single question:
```bash
python main.py --llm YOUR_LLM_NAME --dataset mimic_iii --data_path YOUR_DATA_PATH --logs_path YOUR_LOGS_PATH --debug --debug_id QUESTION_ID_TO_DEBUG
```

For **eICU** dataset, just change the option of dataset to ``--dataset eicu``.

### Citation
If you find this repository useful, please consider citing:
```bibtex
@inproceedings{shi-etal-2024-ehragent,
    title = "{EHRA}gent: Code Empowers Large Language Models for Few-shot Complex Tabular Reasoning on Electronic Health Records",
    author = "Shi, Wenqi  and
      Xu, Ran  and
      Zhuang, Yuchen  and
      Yu, Yue  and
      Zhang, Jieyu  and
      Wu, Hang  and
      Zhu, Yuanda  and
      Ho, Joyce C.  and
      Yang, Carl  and
      Wang, May Dongmei",
    editor = "Al-Onaizan, Yaser  and
      Bansal, Mohit  and
      Chen, Yun-Nung",
    booktitle = "Proceedings of the 2024 Conference on Empirical Methods in Natural Language Processing",
    month = nov,
    year = "2024",
    address = "Miami, Florida, USA",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2024.emnlp-main.1245",
    doi = "10.18653/v1/2024.emnlp-main.1245",
    pages = "22315--22339",
    abstract = "Clinicians often rely on data engineers to retrieve complex patient information from electronic health record (EHR) systems, a process that is both inefficient and time-consuming. We propose EHRAgent, a large language model (LLM) agent empowered with accumulative domain knowledge and robust coding capability. EHRAgent enables autonomous code generation and execution to facilitate clinicians in directly interacting with EHRs using natural language. Specifically, we formulate a multi-tabular reasoning task based on EHRs as a tool-use planning process, efficiently decomposing a complex task into a sequence of manageable actions with external toolsets. We first inject relevant medical information to enable EHRAgent to effectively reason about the given query, identifying and extracting the required records from the appropriate tables. By integrating interactive coding and execution feedback, EHRAgent then effectively learns from error messages and iteratively improves its originally generated code. Experiments on three real-world EHR datasets show that EHRAgent outperforms the strongest baseline by up to 29.6{\%} in success rate, verifying its strong capacity to tackle complex clinical tasks with minimal demonstrations.",
}
```
