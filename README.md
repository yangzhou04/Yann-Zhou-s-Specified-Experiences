**Detailed Experiences**

**Basic Information**

Name: Yang Zhou

Email: yangzhou04@gmail.com

Tel: +86 17780536350

AntGroup Nickname: Yu Guan(羽冠)

Department in charge: Financial Management and Human Resource Data services (17 staff including me + 8 outsource)

Job Code:

- Engineer-data
  - **ETL and modelling**: This is not confined to ETL development but focuses more on the ability of data modelling or data architecture. It studies data transmission and analyses its efficiency and stability. It increases users' experience.
- **Engineer-Applied Algorithm**

Level: 16

Work Location: Sichuan, Chengdu, China

Contracting Company: Ant Rongxin (Chengdu) Network Technology Co., Ltd.

**Education Information**

2007.9-2011.7 Sichuan University, Master's Degree in Software Engineering

2011.9-2014.7 Sichuan University, Bachelor's Degree in Computer Science, research direction is NLP and ML, specifically in Topic Models

Online Learning: Coursera: <https://github.com/yangzhou04/certificate> Machine Learning, Computing for Data Analysis

**Experiences**

**2014.7-2016.7 Algorithm Engineer**

Joined Team named Users' Behaviour Mining

- Users' Behaviour Mining - ID Mapping

S: Life utility payment is an electronic payment industry that assists users in completing electricity and water bill payments on the Alipay app. During the market phase, it is necessary to identify the target audience. However, Alipay's User Behaviour data needs to provide more insights. Alipay procured payment data from power companies, including users' names, IDs, addresses, and phone numbers to address this. Consequently, it is necessary to integrate the payment data from the power companies with Alipay's user data system to supplement the life utility payment labels.

T: Build an ID-mapping system using basic information about users to help the marketing department increase the MAU(Monthly Active Users)

A:

- Understand the marketing strategy and how they define the success indicators: Conversion rate = the portion of users clicking the SMS ad link. MAU and conversion rates are correlated because Chinese users pay their electricity bills monthly.
- Math Modelling: Give two datasets. The first has attributes like name, ID, address, and phone number. The second has Alipay's user_id, ID, phone number and address. Fuse these two datasets into one and supplement another label called 'Life utility payment' to the second dataset with high precision and recall.
- Understand the dataset, especially its quality and make the explanation reasonable.
  - Data Integrity Check: Calculate missing value distributions, except for addresses; others' missing values are incredibly high because the information protects the Chinese's thoughts.
  - Duplicate Value Check: Calculate duplicate value distributions; name attributes are relatively high.
  - Outlier Check: Check if some cases in the text are incredibly long and could crash the pipeline.
  - Data Format Check: Randomly sample a dataset to check users' input behaviour, such as Full-width Pinyin vs. Half-width Pinyin.
- Label datasets
  - Under the authorisation, I used my colleagues' information to label the datasets.
- Feature Engineering and Experiments
  - Geocoding converts two addresses into latitude and longitude, so the distance should make sense.
  - Experiments and preprocessing optimisation: Full-width Pinyin to Half-width, upper letter to lower, traditional Chinese to Simplified, Chinese numbers to Arabic, and spatial symbol translates.
- Deploy and maintenance
  - Use KD-Tree to accelerate the distance-calculating process.
  - Monitor precision and recall, warning if they unexpectedly drop.
- Marketing User Experience suggestions
  - Design a notice panel to inform users and affirm the matching process.

R: Based on a precision = 97% and recall = 85%, the Conversion rate rises from 6% to 42%.

Patent：CN 106598965 A、EP3364309A1、JP2018537760A、SG11201803052QA、KR1020180069869A、US20180232206A1、US20200125327A1

Joined Team named Customers' Experience Improving

- Customers' Problem Recognition

S: When users encounter issues while using the Alipay app, they seek assistance from customer service through various channels, such as online chat or hotlines, using both voice and text. Due to the massive number of Alipay's global users, it's impractical for customer service to review all help requests manually. Therefore, there is a need for a method to help product managers automatically identify user problems.

T: Finding customers' problems, choosing representative keywords and related original voices to help improve the product.

A:

- Understand the product designer's requirements. This situation is open-minded. I have regular meetings with PD to discover their needs interactively. During the process, I figured out that they only want to be noticed when new problems affect large groups of people.
- Math Modelling: Given unlabelled datasets in the forms of voices and texts, clustering them occasionally and finding the new clusters tracing back to original texts.
- Use Alipay's voice-to-text tools to convert voices.
- Use LDA(Latent Dirichlet Allocation) to build a baseline. Modify it to Coupled-LDA to form a (who asks, what questions) tuple.
- Fix some initial words' distributions called seeds to update Coupled-LDA to Centralized-Couplued-LDA labelling old questions and improve the conversation efficiency with PD.
- Regular meetings and suggestions

R: I discovered three new problems in the payment process, which PD accepted.

Patent: CN 106971306 A

**2016.7-2018.7 Senior Algorithm Engineer**

Joined team named Operation of Customers' Fund Department

- Payment Tools Recommendation

S: The payment success rate and the system comeback time are two essential indicators that measure Alipay's user payment experience, especially in protocol payment scenarios when users have multiple bank cards; it will take seconds to get a successful payment. Therefore, regarding product design, limiting round-robin payment to a maximum of one bank card is required while not significantly affecting the payment success rate.

T: Design an automatic decision model that chooses a bank card when a user uses round-robin payment without significantly affecting the success rate.

A:

- Understand the requirements and how they define the success indicators: payments' successful ratio limit to round-robin payment to a maximum of one bank card.
- Math Modelling: Using classification methods, predict the card's successful payment probability given a user's historical payment records.
- Feature Engineering and Experiments:
  - Divide users' payment records into two parts based on a timeline.
  - Using FRM to aggregate users' payment records to do feature engineering, which forms training and testing sets
  - Train a random forest model to predict future behaviour.
- Deployment:
  - Use all FRM features to train an RF model and build an online service using Alipay's platform.
  - Nest the service into the user's payment process.

R: Compared to manual operation, increasing the payment successful rate to 3pt

Patent：HK40010770A、CN 110033247 A、TW202026975A、HK1241511A、CN 107066518 A

**2018.7-2021.7 Algorithm Expert**

- Intelligence RCA of System running failures

S: The Alipay app's high availability relies on the stability of its core systems. As the core systems involve thousands of sub-modules, manual troubleshooting can be time-consuming when issues occur. Therefore, algorithmic methods are needed to aid in locating and resolving problems efficiently, thereby accelerating the process and improving efficiency.

T: When the monitoring indicator drops, find which sub-modules/interfaces' malfunctions are the root cause.

A:

- Understand the requirements: The stakeholder claimed that this project is an innovative RCA system that needs to discover new thoughts in our company. After some investigation, I suggest we develop a Parameters-level RCA system. The main idea is to cluster the regular system log, compare the malfunction log to the regular one, and print out the different parameters.
- I am using SimHash to group similar regular logs quickly.
- Extract parameters describing invokes from logs to form a JSON format.
- When the monitoring indicator drops, compare target malfunction JSON parameters to regular ones and print out the difference.

R: Successfully discovered one malfunction in the parameterised level and reported the result in BU-level

Patent： CN 108712284 A

Joined team named Financial Information System

- Building Financial data services to support Strategical Decision

S: Explaining the business implications behind the fundamental indicator changes in the three primary financial statements is essential to assisting the company in profitability and shareholder management. Therefore, providing relevant financial data services to support analysis is necessary. Profitability, a crucial focus, should be addressed as a priority.

T: Building Financial Data Services to support SSC, FP&A, and business partners in analysing AntGroup's budget and performance as a Project Leader with seven staff.

A:

- Ask FP&A, SSC and Financial BP questions to determine customer needs.
- Design a sustainable solution for the team and maintain the relationship with customers.
- Design the architecture of the whole system and assign modules and tasks to team members.
- Build a financial management data warehouse based on AntGroup's platform called ODPS and Dataworks.
- Construct financial management Indicators and report Systems.
- Support customers in writing notes to explain the trends.
- Help maintain the stability of the whole system.
- Help the career improvement of our team members.
- Give Solution Presentation to our customers' leader.
- Give performance suggestions to the team leader.

R: Help customers explain 91% of income trend reasons to the business product level. 99.9% report stability. 2 team members got promoted from 12 to 14.

**2021.7~present Data Engineer Staff Manager**

A literal Team leader of Financial Accounting Management and Human Resource Data Services(17 staffs+8 outsourced)

S: AntGroup has a net profit of over 50 billion, supported by over 7,000 products and 27000 deployed units. It has a financial management business group with over 300 staff. Data service is critical to the success of Financial planning and analysis. My mission is to provide stable, comprehensive, insightful, and easy-to-use data services to the Financial management business group.

T: Led the team to build Financial data services, including data models, predicting and optimisation algorithms, data products to serve the CEO, CFO, CPO, etc., and FP&A, Treasury, BI, and SSC users’ requirements.

A:

- Design the long-term (3 years) goals and choose strategic indicators to measure the process.
- Design the Data Architecture to support long-term goals.
- Building a team assigns models to suited staff to make things above come true, padding the rest of the work by myself.
  - Team Management and Human Capabilities Growing, such as OKR design and coaching.
  - Project Management
  - Performance Monitoring
- Cooperate with others, do a win-win and Make a more significant credit.
  - Speech and report

R:

- We built a data warehouse that could explain the fluctuating behaviour of profit indicators, including over 90% of income. The data warehouse consists of External Indicators bundles, Financial Business Models, Financial Risk Models, and Financial PL/BS/CF Models.
- We built predicting algorithms such as time series to help users make fund daily plans and automatically classify funds.
- We built optimisation algorithms such as linear optimisation to make investigation plans.
- The stability of our data services is 99% all over the year.
- More than 90% successful promoted ratio in my team.

I wrote a series of articles about Financial Accounting Management in Action on AntGroup's ATA technical blog, and the impact factor is over 94% of colleagues in the same BG(thousands of people).

I, as a co-author, wrote Sections 1 and 2, Chapter 8 of a book named &lt;Integrated Business and Finance-The Financial Technology Architecture of Ant Group&gt;

**Attachment**

Forty-six patents applied to over 13 countries/areas/organs: CN 106598965 A, EP3364309A1, WO/2017/063531, CN 106327000 A, HK40039814A, CN 107368281 A, CN 109598364 A, CN 108470242 A, IN201817017660A, CN 111898148 A, JP2018537760A, CN 107403311 A, CN 108712284 A, CN 110221917 A, CN 109582705 A, SG11201803052QA, HK1241511A, CN 107239438 A, CN 106487939 A, HK40010770A, WO2020147480A1, CN 110262950 A, CN 110245934 A, HK1234916A, CN 110020769 A, CN 108563548 A, CN 110033252 A, CN 109583475 A, WO2019179248A1, CN 110008077 A, KR1020180069869A, US20180232206A1, CN 110033130 A, CN 109919357 A, CN 110008079 A, CN 110033247 A, CN 109063886 A, CN 110019988 A, TW201941058A, CN 109063947 A, CN 110163471 A, CN 108734304 A, CN 109325052 A, WO2020140697A1, CN 108762959 A, CN 109325127 A, WO2019214311A1, CN 110058977 A, CN 106897334 A, CN 108681966 A, CN 109634819 A, US20200125327A1, CN 110032463 A, CN 106971306 A, CN 106897262 A, CN 110046179 A, TW201947446A, CN 109614299 A, TW202026975A, HK40010773A, CN 108762908 A, WO2020155788A1, CN 110390425 A, CN 110222936 A, CN 109919744 A, CN 107066365 A, CN 108763059 A, CN 107066518 A

AntGroup's Job responsibilities:

- Engineer-data
  - **ETL and modelling**: This is not confined to ETL development but focuses more on the ability of data modelling or data architecture. It studies data transmission and analyses its efficiency and stability. It increases users' experience.
  - Data Mining: Builds data models through data mining (SPSS, SAS, etc.). Discovering the value of data—the rules behind it—and applying them to actual business situations can help increase efficiency. Develops complicated data models and deploys them.
  - Data Management: Ensures data security and quality through standardised procedures and systems. Manages data from different dimensions, for example, defines permissions according to users' level. Works out the procedures and solutions accordingly.
  - Data Mining: Makes algorithm breakthroughs and further develops platforms on this basis.
  - Data Visualisation: Analyses the features of the company's data. Designs and develops data visualisation products.
- Engineer-Algorithm
  - Base Common Algorithm-Base Algorithm: Understands the principles of algorithms in a particular area, such as NLP, machine learning, data mining, etc. Responsible for or participated in developing, optimising, and innovating basic models, tools, and software packages. Operates and maintains these products.
  - Base Common Algorithm-Platform Architect: Designs architectures, makes technical regulations and develops core modules for public algorithm service platform. Operates and maintains the systems, such as recommendation system architecture and parallel computing platform.
- **Engineer-Applied Algorithm**

2021.12 expanded extra to Treasure Management Data Services(13 staff)

2022.3 expanded extra to Tax Management Data Services(13 staff)

2022.9 expanded extra to Human Resource Management Data Services(17 staffs+8 outsourced)
