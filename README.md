<!DOCTYPE html>
<html lang="ja" data-theme="light">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>コンセプトメイキング完全解説マニュアル</title>
    <!-- Pico.css -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@picocss/pico@1/css/pico.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Shippori+Mincho:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
      /* --- 基本設定 --- */
      :root {
        --primary-color: #8e5e68;
        --secondary-color: #d4a5a5;
        --accent-color: #2c3e50;
        --text-color: #333333;
        --bg-paper: #fcfcfc;
        --font-main: 'Shippori Mincho', 'Yu Mincho', serif;
      }

      /* 【重要】PCでのスクロール基点 */
      html {
        overflow-x: auto;
        overflow-y: hidden;
        height: 100vh;
        writing-mode: vertical-rl; /* 縦書き */
      }

      body {
        font-family: var(--font-main);
        color: var(--text-color);
        background-color: #f5f5f5;
        margin: 0;
        padding: 0;
        text-orientation: mixed;
        height: 100%;
        /* PCではbodyでのスクロールを無効化（ボタン操作のため） */
        overflow: hidden; 
      }

      /* 画面表示用のレイアウト */
      .book-wrapper {
        background-color: var(--bg-paper);
        height: 95vh;
        margin: 2.5vh auto;
        padding: 4rem 3rem;
        box-sizing: border-box;
        box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
        column-fill: auto;
        column-width: 85vh;
        column-gap: 6rem;
        font-size: 11pt;
        line-height: 1.9;
        text-align: justify;
      }

      /* セクション（章） */
      section {
        margin-left: 6rem;
        display: inline-block;
        vertical-align: top;
        height: 85vh;
        position: relative;
      }

      /* --- 見出し設定 --- */
      h1, h2, h3, h4 {
        font-family: var(--font-main);
        font-weight: 700;
        line-height: 1.5;
      }

      h1.chapter-heading {
        font-size: 2.0rem;
        color: var(--primary-color);
        border-right: 5px solid var(--secondary-color);
        padding-right: 0.8rem;
        margin-left: 3rem;
        margin-top: 0;
        letter-spacing: 0.1em;
      }

      h2 {
        font-size: 1.4rem;
        color: var(--accent-color);
        border-left: 1px solid var(--secondary-color);
        border-right: 1px solid var(--secondary-color);
        padding: 0.8rem 0;
        margin-left: 2rem;
      }

      h3 {
        font-size: 1.2rem;
        font-weight: 700;
        margin-left: 1.5rem;
        color: var(--primary-color);
      }
      h3::before {
        content: '◆';
        font-size: 0.8em;
        margin-bottom: 0.5em; 
        display: inline-block;
      }

      p { margin-left: 1em; text-indent: 1em; }

      /* --- 装飾パーツ --- */
      .highlight-box {
        background-color: #fffaf0; border: 1px solid var(--primary-color); border-radius: 4px; padding: 1.5rem; margin: 1.5rem 0.5rem;
      }
      .point-check {
        border: 3px double var(--secondary-color); padding: 1.5rem; margin: 1.5rem 0; background-color: #fff; position: relative;
      }
      .point-check strong {
        color: var(--primary-color); display: block; font-size: 1.1em; margin-left: 0.5em; border-bottom: 1px dashed #ccc; padding-bottom: 0.5em; margin-bottom: 0.5em;
      }
      .worksheet-table {
        border: 2px solid #333; padding: 1rem; margin: 1rem 0; font-size: 0.9em;
      }
      .worksheet-table table { width: 100%; border-collapse: collapse; }
      .worksheet-table th, .worksheet-table td { border: 1px solid #999; padding: 0.5rem; vertical-align: top; }
      .worksheet-table th { background-color: #eee; color: var(--accent-color); }
      
      /* --- 縦中横 --- */
      .tcy { 
        text-combine-upright: all; 
        -webkit-text-combine: horizontal;
        font-family: sans-serif; 
        margin: 2px;
        display: inline-block;
        font-feature-settings: "pkna";
      }
      
      ol {
        list-style: none; padding: 0; margin: 0;
      }
      ol li {
        margin-top: 0.5rem; margin-left: 1rem; text-indent: -2.2em; padding-top: 2.2em; 
      }

      /* --- 表紙画像 --- */
      .cover-page {
        border: none; padding: 0; background: none; box-sizing: border-box;
        display: flex; flex-direction: column; justify-content: center; align-items: center;
        height: 100%;
      }
      .cover-img {
        max-height: 100%; max-width: 100%; width: auto; height: auto;
        object-fit: contain; box-shadow: 5px 5px 15px rgba(0,0,0,0.3);
      }

      /* --- 目次 --- */
      .toc-list { list-style: none; padding: 0; }
      .toc-list li { 
        margin-left: 0.8rem; border-left: 1px dotted #ccc; padding-left: 0.5rem; 
        display: flex; justify-content: flex-start; align-items: baseline; gap: 1em; text-indent: 0; padding-top: 0;
      }
      .toc-chapter { font-weight: bold; color: var(--primary-color); font-size: 1.1em; white-space: nowrap; }

      .page-header { position: absolute; top: -2rem; right: 0; font-size: 0.8rem; color: #999; }

      /* --- 画面用ボタン（PCのみ表示） --- */
      .nav-button {
        position: fixed; bottom: 20px; z-index: 1000;
        background-color: var(--primary-color); color: white; border: none; border-radius: 50%;
        width: 60px; height: 60px; font-size: 1.5rem; cursor: pointer;
        display: flex; align-items: center; justify-content: center; opacity: 0.9;
        box-shadow: 0 4px 10px rgba(0,0,0,0.3);
        transition: transform 0.2s;
      }
      .nav-button:hover { opacity: 1; transform: scale(1.1); }
      .btn-next { left: 30px; } .btn-prev { right: 30px; }


      /* ▼▼▼ スマホ向け調整 (768px以下) ▼▼▼ */
      @media screen and (max-width: 768px) {
          /* ★重要：スマホではスクロールロックを解除して指で動かせるようにする */
          html {
              overflow-x: scroll; /* スクロール許可 */
              -webkit-overflow-scrolling: touch; /* iPhoneで滑らかに */
          }
          body {
              overflow: visible; /* bodyのロック解除 */
              height: 100%;
          }

          /* 表紙を非表示 */
          .cover-page { display: none !important; }
          
          /* ボタンを非表示 */
          .nav-button { display: none !important; }
          
          /* 読みやすいように余白調整 */
          .book-wrapper {
              height: 100vh;
              margin: 0;
              padding: 4rem 1rem; /* 上下の余白を確保 */
              box-shadow: none;
              font-size: 10.5pt;
          }
      }


      /* ▼▼▼ 印刷レイアウト調整（A5完全対応版） ▼▼▼ */
      @media print {
        @page { size: A5; margin: 15mm; }
        html { height: auto; overflow: visible; }
        body { height: auto; overflow: visible; background: none; font-size: 10.5pt; }

        .book-wrapper {
          width: 100%; height: auto; box-shadow: none; margin: 0; padding: 0;
          display: block; column-count: auto; column-width: auto;
        }

        section {
          break-before: page; break-after: auto; height: auto;
          margin-left: 0; margin-bottom: 0; display: block; position: relative;
        }
        
        /* 印刷時は表紙を必ず表示 */
        section.cover-page {
          break-before: auto; break-after: page;
          display: flex !important; align-items: center; justify-content: center;
          margin: 0; width: 100%; height: 98vh; overflow: hidden;
        }
        
        .cover-img {
          max-width: 100%; max-height: 100%; width: auto; height: auto;
          object-fit: contain; box-shadow: none;
        }

        h1, h2, h3 { break-after: avoid; break-inside: avoid; page-break-after: avoid; }
        h1.chapter-heading { margin-top: 0; padding-top: 1rem; }

        .highlight-box, .point-check, .worksheet-table { break-inside: avoid; }
        .nav-button, .page-header { display: none; }
      }
    </style>
</head>
<body>

<div class="book-wrapper">

    <!-- ■ 表紙（画像） ■ -->
    <!-- スマホではCSSで非表示になります -->
    <section class="cover-page">
        <img src="cover.jpg" alt="表紙" class="cover-img">
    </section>

    <!-- ■ はじめに ■ -->
    <section>
        <h1 class="chapter-heading">はじめに：<br>なぜ、今コンセプトメイキングなのか？</h1>

        <h3>このマニュアルを手にした「あなた」へ（私からのメッセージ）</h3>
        <p>こんにちは。この「コンセプトメイキング完全解説マニュアル」を手に取ってくださり、本当にありがとうございます。この出会いに、まずは感謝させてください。</p>
        <p>今、あなたの手元にあるこの一冊は、単なるノウハウ集ではありません。これは、私自身がビジネスの現場で悩み、もがき、そして見つけ出した「売れる仕組みの核心」へと至る思考の旅路を、あなたと共有したいという想いを込めて書き記したものです。</p>
        <p>もしかしたらあなたは今、新しいビジネスのアイデアに胸を膨らませているかもしれません。あるいは、愛情を込めて育ててきた事業を、もっと多くの人に知ってもらい、次のステージへと押し上げたいと願っているかもしれませんね。もしかすると、「こんなに頑張っているのに、なぜか成果が出ない…」そんな壁に直面し、突破口を探している最中かもしれません。</p>
        <p>どのような状況であれ、きっとあなたは、真剣にビジネスと向き合い、より良い未来を切り拓こうとされているはずです。その熱意と行動力に、私は心からの敬意を表します。</p>

        <h3>私も深くハマった「頑張っているのに報われない」迷宮</h3>
        <p>少し、私の話をさせてください。今でこそ、コンセプトの重要性について語る立場にありますが、かつての私は、まさに「頑張っているのに報われない」迷宮のど真ん中でもがいていました。</p>
        <div class="highlight-box">
            <p>「これだけ高品質な製品を作ったんだ。絶対に顧客は価値を分かってくれるはずだ」<br>
            「競合よりも優れたサービスを提供している。黙っていても選ばれるに違いない」</p>
        </div>
        <p>そんな風に、自社の提供するものへの自信だけを頼りに、市場へと乗り込んでいきました。寝る時間を削り、持てる力のすべてを注ぎ込んだプロジェクトもありました。しかし、現実は甘くありませんでした。鳴かず飛ばず、という言葉がまさにぴったりな状況が続いたのです。顧客からの反応は鈍く、売上は伸び悩み、焦りと不安だけが募っていく日々…。</p>
        <p>なぜだ？ 何が足りないんだ？ 自問自答を繰り返す中で、ある一つのシンプルな、しかし決定的な事実に気づかされたのです。それは、「自分が届けたい価値」と「顧客が本当に求めている価値」の間に、深い溝があったということ。そして、その溝を埋めるための「羅針盤」を持っていなかったということでした。</p>
        <p>その羅針盤こそが、「コンセプト」だったのです。</p>

        <h3>時代が変わっても色褪せない「ビジネスの原点」</h3>
        <p>世の中は、息つく暇もないほどのスピードで変化しています。新しい技術が生まれ、人々の価値観も多様化し、ビジネスを取り巻く環境は複雑さを増すばかりです。</p>
        <p>しかし、どれだけ時代が移り変わろうとも、ビジネスが成り立つ上での「原点」は、決して揺らぐことはありません。それは、<strong>「誰かの困りごとや願いを見つけ出し、それを解決することで、より良い状態へと導くこと」</strong>。ただ、それだけなのです。</p>
        <p>コンセプトメイキングとは、このビジネスの原点に立ち返り、「自社は、誰の、どんな課題を解決し、どんな未来を提供する存在なのか？」という根本的な問いに、明確な答えを与えるプロセスです。それは、単にお洒落なキャッチコピーを考えたり、目先の売上を追うための小手先のテクニックではありません。自社の存在意義そのものを深く掘り下げ、顧客との間に、一時的な関係ではない、深く、永続的な繋がりを築くための、いわば「魂を込める作業」なのです。</p>

        <h3>このマニュアルが、あなたの「武器」になるために</h3>
        <p>このマニュアルでは、コンセプトメイキングという、一見すると捉えどころのないテーマを、具体的なステップと、現場で即使える思考法に分解してお伝えしていきます。私が経験した失敗や、そこから学んだ教訓も、包み隠さずお話しするつもりです。</p>
        <p>読み進めるうちに、あなたはきっと、</p>
        <ul>
            <li>価格競争や品質至上主義の「本当の危うさ」を理解し、</li>
            <li>顧客の心の奥底にある「真の欲求」を読み解く視点を手に入れ、</li>
            <li>数多ある競合の中で、自社が「選ばれるべき理由」を明確に言語化し、</li>
            <li>顧客の心を揺さぶり、行動を促す「響くメッセージ」を紡ぎ出し、</li>
        </ul>
        <p>そして何より、自信を持って自社の価値を世に問い、ビジネスをドライブさせるための「揺るぎない軸」を、ご自身の中に打ち立てることができるはずです。</p>
        <p>このマニュアルが、あなたのビジネスにとって、強力な「武器」となり、未来を切り拓くための一助となることを、心から願っています。</p>
        <p>さあ、準備はよろしいでしょうか？<br>共に、コンセプトメイキングという刺激的な冒険へと、出発しましょう。</p>
    </section>

    <!-- ■ 目次 ■ -->
    <section>
        <h1 class="chapter-heading">目次</h1>
        <ul class="toc-list">
            <li><span class="toc-chapter">はじめに</span> <span>なぜ、今コンセプトメイキングなのか？</span></li>
            <li><span class="toc-chapter">第<span class="tcy">1</span>章</span> <span>幻想から目を覚ます</span></li>
            <li><span class="toc-chapter">第<span class="tcy">2</span>章</span> <span>コンセプトの本質 ～顧客は何を買っているのか？～</span></li>
            <li><span class="toc-chapter">第<span class="tcy">3</span>章</span> <span>すべての始まりは「顧客理解」から</span></li>
            <li><span class="toc-chapter">第<span class="tcy">4</span>章</span> <span>売れるコンセプトの源泉「顧客の問題」を発掘する</span></li>
            <li><span class="toc-chapter">第<span class="tcy">5</span>章</span> <span>響く価値提案「ベネフィット」を定義する</span></l
