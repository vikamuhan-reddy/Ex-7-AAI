<H3>ENTER YOUR NAME : Vikamuhan reddy</H3>
<H3>ENTER YOUR REGISTER NO. 212223240181</H3>
<H3>EX. NO.7</H3>
<H3>DATE:18/05/25</H3>
<H1 ALIGN =CENTER>Implementation of Text  Summarization</H1>
<H3>Aim:
To perform automatic text summarization using Natural Language Processing (NLP) techniques. </H3> 
 <BR>
<h3>Algorithm:</h3>
Step 1 Import necessary libraries for natural language processing tasks.<BR>
Step 2: Download NLTK resources, including the punkt tokenizer and stopwords.<BR>
Step 3: Define Text Preprocessing Function to tokenize, remove stopwords, and perform stemming.<BR>
Step 4: Define the Text Summarization Function using a simple frequency-based approach.<br>
    - Calculate the frequency of each word in the preprocessed text.<br>
    - Calculate a score for each sentence based on the sum of word frequencies.<br>
    - Select the top N sentences with the highest scores to form the summary.<br>
Step 5: Construct the main program to read the paragraph  and perform text summarization<br>
      - Generate and print the original text.<br>
      - Generate and print the text summary using the  Text Summarization function<br>
<H3>Program:</H3>


```py
!pip install nltk

import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize, sent_tokenize
from nltk.stem import PorterStemmer

# Download the necessary NLTK data
nltk.download('punkt')
nltk.download('stopwords')
nltk.download('punkt_tab') # Added this line to download the required resource

def preprocess_text(text):

    words = word_tokenize(text)

    stop_words = set(stopwords.words('english'))
    filtered_words = [word for word in words if word.lower() not in stop_words and word.isalnum()]

    stemmer = PorterStemmer()

    stemmed_words = [stemmer.stem(word) for word in filtered_words]
    return stemmed_words

def generate_summary(text, num_sentences=3):

    sentences = sent_tokenize(text)
    preprocessed_text = preprocess_text(text)

    word_frequencies = nltk.FreqDist(preprocessed_text)

    sentence_scores = {}
    for sentence in sentences:
        for word, freq in word_frequencies.items():
            # Checking if the word is in the sentence (case-insensitive)
            if word in sentence.lower():
                if sentence not in sentence_scores:
                    sentence_scores[sentence] = freq
                else:
                    sentence_scores[sentence] += freq

    # Sorting sentences by their score in descending order and selecting the top num_sentences
    summary_sentences = sorted(sentence_scores, key=sentence_scores.get, reverse=True)[:num_sentences]

    return ' '.join(summary_sentences)

if __name__ == "__main__":
    input_text = """
    Artificial Intelligence (AI) encompasses various subfields aimed at enabling machines to mimic human intelligence. 
    One such subfield is Natural Language Processing (NLP), which focuses on developing algorithms and models that allow computers to understand, interpret, and generate human language.
     NLP powers applications like chatbots, language comprehension systems, and text generation tools. 
     This project demonstrates a basic AI technique for text summarization using NLP methods.
  """

    summary = generate_summary(input_text)
    print("Origina1 Text: ")
    print(input_text)
    print(" \nSummary : ")
    print(summary)
```



<H3>Output</H3>

<img width="1218" alt="Screen Shot 1947-02-28 at 13 57 35" src="https://github.com/user-attachments/assets/1d655d99-8977-483e-b3eb-600d7403fbfe" />



<H3>Result:</H3>
Thus ,the program to perform the Text summarization is executed sucessfully.


